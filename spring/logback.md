## `Logback` 
> #SLF4J #LOGBACK #LOGGING #LOG <BR>
> [참고 자료](https://tecoble.techcourse.co.kr/post/2021-08-07-logback-tutorial/) <br>
> [영상 자료](https://www.youtube.com/watch?v=JqZzy7RyudI)
  
- 기존 로깅 프레임워크 의문이 많기에???
- `SLF4J`의 구현체
- `Log4J`를 토대로 만든 프레임워크
- 현재 logback 많이 사용✔
- 스프링 프레임워크에서 채택 >> `SLF4J` `Logback` ✔
![image](https://user-images.githubusercontent.com/61215550/166345668-b1eef536-655c-4384-ba47-c4ccc9d8f261.png)

  
### 1. 로깅⭐
- 시스템이 동작할 때 __시스템의 상태__ 및 __동작 정보__ 를 시간 경과에 따라 기록하는 것

### 2. 스프링에서 로깅하는 방법
- 초기 `JCL(Jakarta Commons Logging)`
- 최근 `Log4j` `Logback` 으로 스프링 부트의 로그 구현체 사용
#### 2.1 `Log4j`
- 가장 오래된 프레임워크 / Apache의 Java기반 Logging Framework
- `xml` `propreties` 파일 로깅환경 구성
- 콘솔 및 파일 출력의 형태로 로깅 할 수 있게 도움

#### 2.2 `Logback`
- Java 기반 Logging Framework 중 하나로 가장 널리 사용
- `SLF4j` 의 구현체 
- Spring Boot 환경이라면 별도의 dependency 추가 없이 기본적으로 포함✔
- ![image](https://user-images.githubusercontent.com/61215550/166343363-510aea36-8b99-404c-863a-0d0be5e9e733.png)

### 3. 로그 레벨 관련
- `Logback`은 5단계의 로그 레벨 존재
- 심각도 수준 `Error > Warn > Info > Debug > Trace`
- ⭐`Debug` `Trace` 레벨의 로깅은 개발 단계에서만 사용!! 배포 단계에서는 사용하지 말자

|명칭|설명|
|-----|-----|
|`Error`|예상하지 못한 심긱한 문제가 발생한 경우, 즉시 조치를 취해야 할 수준의 레벨|
|`Warn`|로직 상 유효성 확인, 예상 가능한 문제로 인한 예외 처리, 당장 서비스 운영에는 영향 없지만 주의해야할 부분|
|`Info`|운영에 참고할만한 사항, 중요한 비즈니스 프로세스 완료|
|`Debug`|개발 단계에서 사용 / SQL 로깅 가능|
|`Trace`|모든 레벨에 대한 로깅 추적 가능 / 개발 단계에서 사용|

### 4. 로그 파일 작성✔
- 콘솔 로그의 수준 변경하는 방법 2가지
  - `applicaton.yml` : 난이도 쉽지만 실제 제품 및 세부적인 설정에는 불편
  - `logback-spring.xml` : 이걸로 관리하는 편이 좋다 📌

![image](https://user-images.githubusercontent.com/61215550/166345308-5330bdf5-b5e8-4b35-9437-925d96548f64.png)
  
---
## Logback
> [참고 자료](https://livenow14.tistory.com/64)
### 1. 설정 요소
- `Logger`: 어떻게 기록
  - 기본 레벨 = `trace`
  - `trace < debug < info < warn < error`
- `Appender`: 어디에다 기록
  - 로그 메세지가 출력할 대상 결정
- `Layout`: 어떻게 출력
  - 사용자가 지정한 형식으로 표현 될 로그메시지를 변환하는 역할
  - 현재는 encoder 사용!!

### 2. 실습 요구사항⭐
- 테스트, 개발 환경: INFO레벨 로그 >> `Console` 에다
- 프로덕션 환경: INFO, WARN, ERROR >> `FILE` 남기기

  
