## `Log` 로그
- 빠르게 장애 지점 파악 및 어떤 이유로 발생했는지 파악하기 위해 로깅 사용
### Log 란
- 소프트웨어가 실행되는 동안의 기록 의미 >> 이러한 행위 >> __로깅__ ✔
- 유명한 로깅 라이브러리 목록
  - `JCL` `slf4j` `log4j` `logback` 등등

### SLF4J
- 추상화된 로깅 라이브러리
  - 구현체 필요!!
- 3가지 모듈로 구성
  1. `API`: 로깅 인터페이스
  2. `Binding`: 여러 로거로 연결해주는 일/...
  3. `Bridge`: 레거시 코드를 위한 모듈

### 1. 사용법
- `slf4j` 2가지 사용법
  1. `logger` 직접 생성
  2. 롬복 어노테이션 `@slf4j`

#### 1-1. 직접 생성
```java
public class LoggerTest{
  private static final Logger logger = LoggerFactory.getLogger(LoggerTest.class);
}
```

### 2. 로그 레벨
- 출력하는 정보에 따라!!!
- `TRACE < DEBUG < INFO < WARN < ERROR < FATAL`
  - `FATAL`: 가장 크리티컬한 에러 발생 시
  - `ERROR` : 요청 처리하는 중 오류가 발생 시
  - `WARN` : 처리 가능한 문제, 시스템 에러의 원인이 될 수 있는 경고성 메시지
  - `INFO` : 상태 변경과 같은 정보성 로그
  - `DEBUG` : 프로그램 디버깅하기 위한 정ㅂ
  - `TRACE` : 추적 레벨은 DEBUG보다 훨씬 자세한 정보 표시(거의 사용 X)
#### 2-1. 팁
- 스프링 부트 사용 시 `application.properties/yml` 통해 간단하게 설정 가능
- 체계적 관리 할 때 `logback-spring.xml` 사용 권장

