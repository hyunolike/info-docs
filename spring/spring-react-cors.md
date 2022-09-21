## `Spring` `React` - CORS 설정 방법
- 크게 2가지
  - React에서 설정
  - Spring Boot에서 설정
- CORS(Cross-Origin Resource Sharing): 다른 출처의 자원을 공유할 수 있도록 설정하는 권한 체제
### `Spring Boot`에서 설정해보자
#### 1. `Configuraton` 설정 - [참고자료](https://github.com/woowacourse-teams/2021-botobo/blob/main/backend/src/main/java/botobo/core/config/WebConfig.java)
```java
@Configuration
public class WebConfig implements WebMvcConfigurer {

    @Value("${cors.allowed.origins:}")
    private String[] allowedOrigins;

    @Override
    public void addCorsMappings(CorsRegistry registry) { ⭐
        registry.addMapping("/**") 📌 URL패턴 정의
                .allowedOrigins(allowedOrigins) 📌 자원 설정
                .allowedMethods("GET", "POST", "PUT", "DELETE", "OPTIONS")
                .allowCredentials(true) 
                .maxAge(3000); 📌원하는 시간만큼 pre-flight 리퀘스트 캐싱
    }

    @Override
    public void addArgumentResolvers(List<HandlerMethodArgumentResolver> resolvers) {
        resolvers.add(searchArgumentResolver());
    }

    @Bean
    public SearchArgumentResolver searchArgumentResolver() {
        return new SearchArgumentResolver();
    }

}
```

#### 2. `yml` 파일 - [참고자료](https://github.com/woowacourse-teams/2021-botobo/blob/main/backend/src/main/resources/application-local-mariadb.yml)
```yml
cors:
  allowed:
    origins: "http://localhost:3000"
```

### (추가) 어노테이션 설정
```java
@RestController
@RequiredArgsConstructor
@CrossOrigin(origins = "http://localhost:3001") ⭐
public class JsoupController {

    private final JsoupService jsoupService;

    @GetMapping("/jsoup/get")
    public String jsoupGet() throws IOException {
        return jsoupService.jsoupGet();
    }

    @GetMapping("/jsoup/post")
    public String jsoupPost() throws IOException {
        return jsoupService.jsuopPost();
    }
}
```
