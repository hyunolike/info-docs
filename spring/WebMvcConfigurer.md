## `WebMvcConfigurer`
> [참고 자료](https://goodgid.github.io/Spring-WebMvcConfigurer/)
- 많은 프로젝트는 `WebMvcConfigurer`를 구현

### 개념
- `@EnableWebMvc` 사용 시 __ViewResolver__ 값 자동 등록!
- 하지만 추가적인 세팅은 `@Bean`을 직접 정의해서 구현해야 된다는 불편함 ㅠ,ㅠ


```java
@Bean
public ViewResolver customViewResolver() {
    InternalResourceViewResolver internalResourceViewResolver = new InternalResourceViewResolver();
    internalResourceViewResolver.setPrefix("/WEB-INF/");
    internalResourceViewResolver.setSuffix(".jsp");
    return internalResourceViewResolver;
}
```

- ⭐ `WebMvcConfigurer` 사용 시 `@EnableWebMvc` 자동적으로 세팅해주는 설정에 개발자가 원하는 설정 추가 가능 
  - `@Override` 가능해짐

### 예시 코드
- Case 1. `WebConfigurer` 구현한 경우 ✔

```java
@Configuration
@ComponentScan
@EnableWebMvc
public class WebConfig implements WebMvcConfigurer {

  // Case1. WebMvcConfigurer를 구현하였을 경우
  @Override
  public void configureViewResolvers(ViewResolverRegistry registry) {
    registry.jsp("/WEB-INF/",".jsp");
  }
}
```

- Case 2. 직접 Bean 정의하는 경우 ✔

```java
@Configuration
@ComponentScan
@EnableWebMvc
public class WebConfig {

  // Case2. WebMvcConfigurer를 구현하지 않고 직접 Bean을 정의하는 경우
  @Bean
  public ViewResolver customViewResolver() {
      InternalResourceViewResolver internalResourceViewResolver = new InternalResourceViewResolver();
      internalResourceViewResolver.setPrefix("/WEB-INF/");
      internalResourceViewResolver.setSuffix(".jsp");
      return internalResourceViewResolver;
    }
}
```
