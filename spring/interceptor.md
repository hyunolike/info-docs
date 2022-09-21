## `Interceptor` 인증 구현
> [참고자료](https://medium.com/@devAsterisk/spring-boot-%EA%B8%B0%EB%B0%98-rest-api-%EC%A0%9C%EC%9E%91-5-bd1b4f0e4680)
- ![image](https://user-images.githubusercontent.com/61215550/191407566-68d7419e-5ef2-495b-9a17-72ef57b01814.png)
- ✔ 위와 같이 Handler(Controller) 수행 전 후의 요청을 intercept 하여 처리할 때 사용!! 

### 과정
1. 인증 담당 부분 개발 `AuthenticationService`
2. 위의 인증 수행하는 `AuthenticationInterceptor` 개발
    - path 별 Interceptor 적용할 범위 지정 가능

### 1. `AuthenticationService`
```java
@Service
@Transactional(readOnly = true)
public class AuthService {

    private final JwtTokenProvider jwtTokenProvider;
    private final UserRepository userRepository;
    private final OauthManagerFactory oauthManagerFactory;
    private final RefreshTokenRepository refreshTokenRepository;

    public AuthService(JwtTokenProvider jwtTokenProvider, UserRepository userRepository,
                       OauthManagerFactory oauthManagerFactory, RefreshTokenRepository refreshTokenRepository) {

        this.jwtTokenProvider = jwtTokenProvider;
        this.userRepository = userRepository;
        this.oauthManagerFactory = oauthManagerFactory;
        this.refreshTokenRepository = refreshTokenRepository;
    }

    @Transactional
    public TokenResponse createAccessToken(String socialType, LoginRequest loginRequest) {
        SocialType socialLoginType = SocialType.of(socialType);
        OauthManager oauthManager = oauthManagerFactory.findOauthMangerBySocialType(socialLoginType);
        User userInfo = oauthManager.getUserInfo(loginRequest.getCode());
        Optional<User> user = userRepository.findBySocialIdAndSocialType(userInfo.getSocialId(), socialLoginType);
        if (user.isPresent()) {
            return TokenResponse.of(jwtTokenProvider.createAccessToken(user.get().getId()));
        }
        User savedUser = userRepository.save(userInfo);
        return TokenResponse.of(jwtTokenProvider.createAccessToken(savedUser.getId()));
    }

    public TokenResponse renewAccessToken(Long id) {
        return TokenResponse.of(jwtTokenProvider.createAccessToken(id));
    }

    @Transactional
    public String createRefreshToken(Long id) {
        String refreshTokenValue = jwtTokenProvider.createRefreshToken(id);
        Long timeToLive = jwtTokenProvider.getJwtRefreshTokenTimeToLive();
        RefreshToken savedRefreshToken = refreshTokenRepository.save(new RefreshToken(id, refreshTokenValue, timeToLive));
        return savedRefreshToken.getTokenValue();
    }

    @Transactional
    public void removeRefreshToken(String refreshToken) {
        try {
            validateRefreshToken(refreshToken);
        } catch (UnAuthorizedException e) {
            return;
        }
        String id = jwtTokenProvider.getStringIdFromPayLoad(refreshToken, JwtTokenType.REFRESH_TOKEN);
        refreshTokenRepository.deleteById(id);
    }

    public Long extractIdByToken(String token, JwtTokenType tokenType) {
        return jwtTokenProvider.getIdFromPayLoad(token, tokenType);
    }

    public AppUser findAppUserByToken(String accessToken) {
        if (accessToken == null) {
            return AppUser.anonymous();
        }
        validateAccessToken(accessToken);
        Long userId = jwtTokenProvider.getIdFromPayLoad(accessToken, JwtTokenType.ACCESS_TOKEN);
        return AppUser.user(userId);
    }

    public void validateAccessToken(String accessToken) {
        jwtTokenProvider.validateToken(accessToken, JwtTokenType.ACCESS_TOKEN);
    }

    public void validateRefreshToken(String refreshToken) {
        jwtTokenProvider.validateToken(refreshToken, JwtTokenType.REFRESH_TOKEN);
        validateStoredRefreshToken(refreshToken);
    }

    private void validateStoredRefreshToken(String refreshToken) {
        String id = jwtTokenProvider.getStringIdFromPayLoad(refreshToken, JwtTokenType.REFRESH_TOKEN);
        RefreshToken storedRefreshToken = refreshTokenRepository.findById(id)
                .orElseThrow(TokenNotValidException::new);
        if (!refreshToken.equals(storedRefreshToken.getTokenValue())) {
            throw new TokenNotValidException();
        }
    }
}
```

### 2. `AuthenticationInterceptor`
```java
@Configuration
public class AuthenticationPrincipalConfig implements WebMvcConfigurer {

    private final AuthService authService;

    public AuthenticationPrincipalConfig(AuthService authService) {
        this.authService = authService;
    }

    @Bean
    public AuthorizationInterceptor authorizationInterceptor() {
        return new AuthorizationInterceptor(authService);
    }

    @Bean
    public PublicAuthorizationInterceptor publicAuthorizationInterceptor() {
        return new PublicAuthorizationInterceptor(authService);
    }

    @Bean
    public AuthenticationPrincipalArgumentResolver authenticationPrincipalArgumentResolver() {
        return new AuthenticationPrincipalArgumentResolver(authService);
    }

    @Override
    public void addArgumentResolvers(List<HandlerMethodArgumentResolver> resolvers) {
        resolvers.add(authenticationPrincipalArgumentResolver());
    }

    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(authPathMatcherInterceptor());
        registry.addInterceptor(publicAuthPathMatcherInterceptor());
    }

    @Bean
    public PathMatcherInterceptor authPathMatcherInterceptor() {
        return new PathMatcherInterceptor(authorizationInterceptor())
                .addPathPatterns("/**", PathMethod.ANY)
                .excludePathPatterns("/", PathMethod.GET)
                .excludePathPatterns("/index.html", PathMethod.GET)
                .excludePathPatterns("/favicon.ico", PathMethod.GET)
                .excludePathPatterns("/error", PathMethod.GET)
                .excludePathPatterns("/**", PathMethod.OPTIONS)
                .excludePathPatterns("/infra/**", PathMethod.GET)
                .excludePathPatterns("/quizzes/**", PathMethod.GET)
                .excludePathPatterns("/login/**", PathMethod.POST)
                .excludePathPatterns("/token/**", PathMethod.GET)
                .excludePathPatterns("/logout", PathMethod.GET)
                .excludePathPatterns("/workbooks/public", PathMethod.GET)
                .excludePathPatterns("/workbooks/public/**", PathMethod.GET)
                .excludePathPatterns("/workbooks/download", PathMethod.GET)
                .excludePathPatterns("/ranks/**", PathMethod.GET)
                .excludePathPatterns("/tags", PathMethod.GET)
                .excludePathPatterns("/users", PathMethod.GET)
                .excludePathPatterns("/search/**", PathMethod.GET);
    }

    @Bean
    public PathMatcherInterceptor publicAuthPathMatcherInterceptor() {
        return new PathMatcherInterceptor(publicAuthorizationInterceptor())
                .addPathPatterns("/workbooks/public/?*", PathMethod.GET);
    }
}
```
