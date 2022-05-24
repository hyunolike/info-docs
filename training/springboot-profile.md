## `spring boot` 환경 별 설정 및 환경 설정
### 1. 개념 정리
- 기존 `spring.profiles` 설정
- `yml` 파일은 하나의 파일안에 환경별 코드 작성 가능! 
  - `properties`는 각각의 파일로 나눠서 작성
- 현재 `spring boot 2.4` 이용 시 >> `spring.profiles` __deprecated__ ⭐
  - `spring.profiles.group.<source>` 이용해 여러 프로파일들 한꺼번에 그룹지어 하나의 프로파일 작성이 가능해짐 ✔
  - 위에꺼 사용 시 프로파일 그룹에 대한 __논리적 이름__ 정의 가능해짐

```yml
spring:
  profiles:
    group:
      "local": "testdb,common" ⭐
      "dev":  "testdb,common"  ⭐
      "prod": "proddb,common"  ⭐


---

spring:
  config:
    activate:
      on-profile: "proddb" ⭐
  datasource:
    url: "jdbc:mysql://service-server/web"
    username: "proddbuser"
    password: "proddbpass"

---


spring:
  config:
    activate:
      on-profile: "testdb" ⭐
  datasource:
    url: "jdbc:mysql://test-server/test"
    username: "dbuser"
    password: "dbpass"
 
---

spring:
  config:
    activate:
      on-profile: "common" ⭐

server:
  port: 8080
  tomcat:
    uri-encoding: UTF-8
```

### 2. 현재 상황
- sftp.properties (외부 프로퍼티파일): 환경별 나눠서 동작 되게 해야됨
- application.yml (환경 파일): 환경별 그룹지어서 실행 가능하도록

### 3. 개발 순서
1. 먼저 `application.yml` 파일 위에 `spring.profiles.group.<source>` 이용해 나눠서 설정
2. 그 다음으로 `sftp.properties` 환경별 설정을 위해 >> `PropertyLocalConfig.java` 에 `@Profile("환경 명")` 제일 상단에 추가 해준다.
3. 끝~~~
