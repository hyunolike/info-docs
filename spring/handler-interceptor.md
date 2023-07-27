## HandlerInterceptor
> [참고자료](https://bamdule.tistory.com/149)
- URL 요청 / 응답 시점 > 가로채서 > 전/후 처리
  - `Interceptor` 시점 > Spring Context & Bean 접근 가능

### 비슷한 역할
- `Filter`
  - Spring framework 무관하게 동작
  - Spring 자원 이용 불가
  - 인코딩 / XSS 방어 등.. 사용
- `AOP`
  - 비즈니스 로직
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/473d0df5-9f7e-4211-9b54-244b3af080c2)

### Interceptor 생성
#### 1. PreHandle
- 컨트롤러 진입전 수행
#### 2. PostHandle
- 컨트롤러 진입 > 뷰 렌더링 시점 수행
#### 3. afterConcurrentHandlingStarted
- 비동기 요청시 > PostHandle & afterCompletion 수행 x > afterConcurrentHandlingStarted 가 수행

### Interceptor 등록
- `WebMvcConfigurer` >   @Override public void addInterceptors(InterceptorRegistry registry)
