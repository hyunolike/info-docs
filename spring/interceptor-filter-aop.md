## 인터셉터, 필터, AOP 차이
> [참고자료](https://goddaehee.tistory.com/154)
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/514a814e-e87a-44b6-86bc-d9f5cedb1fb9)
### 개념
- `Interceptor` `Filter` > Servlet 단위 실행
- `AOP` > Proxy 패턴의 형태로 실행
#### 요청순서
```
Filter -> Interceptor -> AOP -> Interceptor -> Filter
```
#### ✔ Filter 
- 요청과 응답을 거른뒤 정재하는 역할
- 자원 처리 끝난 후 응답내용에 대해서도 변경하는 처리 가능
- 필터 > 스프링 컨텍스트 외부에 존재! 스프링과 무관한 자원에 대해 동작
#### ✔ Interceptor
- 요청에 대한 작업 `전/후` 가로챔
- `DistpatcherServlet` 컨트롤러 호출하기 전, 후 끼어들어!
  - 스프링 컨텍스트 내부에서 Controller에 관한 요청과 응답에 대해 처리
- 스프링의 모든 빈 객체 접근 가능
#### ✔ AOP
- `OOP` 보완하기 위한 개념 😂
- 객체지향 프로그래밍
  - 중복 줄일 수 없는 부분을 줄이기 위함
  - 종단면(관점)에서 바라보고 처리
#### ✔ 주요 차이점
|`Interceptor` `Filter`|`AOP`|
|-|-|
|메서드 전후의 지점에 자유롭게 설정 가능|주소, 파라미터, 에노테이션 등 다양한 방법|
|주소로 대상을 구분해서 걸러야돼!|-|
|`HandlerInterceptor` 파라미터 이거 사용해 아래확인! <br/> `HttpServletRequest` `HttpServletResponse`|`Advice` 파라미터 호출가능|
