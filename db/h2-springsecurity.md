## `H2 DB` + `Spring Security` 함께 사용
> [참고 자료](https://github.com/HomoEfficio/dev-tips/blob/master/Spring%20Security%EC%99%80%20h2-console%20%ED%95%A8%EA%BB%98%20%EC%93%B0%EA%B8%B0.md)
### 1. 인증 면제 처리
- `h2-console` >> `permitAll()` 인증 면제 처리 

### 2. CSRF 면제 처리
- Spring Security >> Cross Site Request Forgery(CSRF) 방지 장치 기본 탑재
- H2 Console 로그인 화면 >> CSRF처리 되지 않기에 에러 발생ㅠ,ㅠ 
- 아룰 위해 `disable` 하는 것은 애플리케이션의 전체 보안 수준이 낮아지기에 비추천
  - H2 db에 대해서만 처리하자

### 3. X-Frame-Options 면제 처리
```java
.and()
.headers().addHeaderWriter(new XFrameOptionsHeaderWriter(XFrameOptionsHeaderWriter.XFrameOptionsMode.SAMEORIGIN))
.and()
```

### 전체 코드
```java
@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
                .authorizeRequests()
                .antMatchers(
                        "/h2-console/**"
                ).permitAll().anyRequest().authenticated()
                .and()
                .csrf()
                .ignoringAntMatchers("/h2-console/**")
                .and()
                .headers().addHeaderWriter(new XFrameOptionsHeaderWriter(new WhiteListedAllowFromStrategy(Arrays.asList("localhost"))))
                .frameOptions().sameOrigin();
    }

    public PasswordEncoder passwordEncoder(){
        return new BCryptPasswordEncoder();
    }
}
```
