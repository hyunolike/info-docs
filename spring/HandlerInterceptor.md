## `HandlerInterceptor`
> [참고 자료](https://bamdule.tistory.com/149)
- Spring Framework 지원하는 기능
- URI 요청, 응답 시점을 기로채서 전/후 처리 하는 역할
- `Interceptor` 시점에 Spring Context, Bean 접근 가능 
- 비슷한 역할 >> `Filter` `AOP` 2가지 존재
  - `Filter`: Spring Framework와 무관하게 동작 / Spring 자원 이용 불가 >> 보통 인코딩, XSS방어 등의 용도
  - `AOP`: 주로 비즈니스 로직에서 실행 / Logging, transaction 처리 등 중복 코드가 발생할 경우 중복 줄이기 위해 사용 / 메소드 처리 전후 지점에 자유롭게 설정 가능

### Filter, Interceptor, AOP의 흐름
![image](https://user-images.githubusercontent.com/61215550/173281121-d37268bf-19bd-4699-ae02-c5f291ab00d8.png)

### 1. `Interceptor` 생성
- `PreHandle(HttpServletRequest request, HttpServletResponse response, Object handler)`
  -  컨트롤러 진입하기 전 실행
  -  반환 값 true일 경우 컨트롤러 진입 / false인 경우 진입 x
  -  Object handler는 진입하려는 컨트롤러 객체 담김
- `PostHandle(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView)`
  - 컨트롤러 진입 후 View가 랜더링 되기 전 수행
- `afterComplete(HttpServletRequest request, HttpServletResponse response, Object object, Exception ex)`
  - 컨트롤러 진입 후 view가 랜더링 된 후에 실행되는 메소드
- `afterConcurrentHandlingStarted(HttpServletRequest request, HttpServletResponse response, Object h)`
  - 비동기 요청 시 PostHandle와 afterCompletion 수행되지 않고 afterConcurrentHandlingStarted 수행

### 2. `Interceptor` 등록
- ✔ WebMvcConfigurer 구현 >> Spring Boot에서 기본적으로 설정 중 `interceptor` 부분 커스텀!


```java
import org.springframework.context.annotation.Configuration;
import org.springframework.web.servlet.config.annotation.InterceptorRegistry;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;

@Configuration
public class WebMvcConfig implements WebMvcConfigurer {

    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(new MyInterceptor())
                .addPathPatterns("/*") // 해당 경로에 접근하기 전에 인터셉터가 가로챈다.
                .excludePathPatterns("/boards"); // 해당 경로는 인터셉터가 가로채지 않는다.
    }
}
```
