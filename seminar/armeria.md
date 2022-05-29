## `Armeria`  
> [공식 홈페이지](https://armeria.dev/) / 깃허브 `line/armeria`
- 어떤 오픈 소스 프로젝트?
- 사용 시 가장 큰 장점
- HTTP, gRPC 동시 지원하는데 실제 사례 및 장점

### 1. 소개
- __단순한 형태__ 로 서버 개발 가능
```java
Server
  .builder()
  .service(
    "/hello",
    (ctx, req) -> HttpResponse.of("Hello!"))
  .service(GrpcService
    .builder()
    .addService(myGrpcServiceImpl)
    .build())
  .service(
    "/api/thrift",
    ThriftService.of(myThriftServiceImpl))
  .service(
    "prefix:/files",
    FileService.of(new File("/var/www")))
  .service(
    "/monitor/l7check",
    HealthCheckService.of())
  .build()
  .start();
```
- 주요 기능
  - `Security` - Authn/z, CORS, SAML
  - `Rate-limiting`
  - `Distributed tracing`
  - `Debugging & management`
  - `<Your custom decorator>`
- ![image](https://user-images.githubusercontent.com/61215550/170850984-26023105-b160-40ac-b750-dc687c674939.png)

### 2. 원칙
- 원칙1. Well-paced >> 단순화 
  - Easy to learn & easy to master
- 원칙2. Unopinionated(integration) >> 1가지가 아닌 2~3가지 통합하는 기술
  - 여러가지 프로토콜 지원해 요새는!! >> 복잡도를 떨어뜨려
  - `gRPC + REST + GraphQL`
  - Load balancer health checks
  - Web Sockets
  - Static resources
- 원칙3. Community-friendly
  - ![image](https://user-images.githubusercontent.com/61215550/170851199-a7ad9fad-3317-40a0-a1d0-e7cf3eba9590.png)
  - 1. 친근한 분위기
  - 2. 자신의 아이디어 컨트리뷰션 도와주는 거
  - 3. 작업 변경 사항 시 프로젝트의 __일관성__ 있게
