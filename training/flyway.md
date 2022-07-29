## Spring Boot + Flyway
> [참고자료](https://sabarada.tistory.com/193)
- 사전 작업
  - DB(아무거나) >> ✔ DB별 버전 지원하는 것도 있으니 주의!

### 개발 순서
#### 1. application.yml 파일 
```yml
spring:
  datasource:
    url: jdbc:mariadb://localhost:3333/mona
    driver-class-name: org.mariadb.jdbc.Driver
    username: mona
    password: 1111
  jpa:
    hibernate:
      ddl-auto: validate
    properties:
      hibernate:
        show_sql: true
        format_sql: true
    generate-ddl: false

  # flyway
  flyway:
    locations: classpath:/db/migration
    sql-migration-suffixes: sql
    baseline-on-migrate: true
    baseline-version: 0
```

#### 2. `sql` 파일
- 명명 규칙 준수해서 ddl 파일 생성 ⭐
- ![image](https://user-images.githubusercontent.com/61215550/181704839-23784984-0dde-484f-a2e5-83c87f8b3697.png)

#### 3. 서버 시작
- ![image](https://user-images.githubusercontent.com/61215550/181704889-e7088d09-5762-40db-bc2c-7ce31e034adf.png)
- ![image](https://user-images.githubusercontent.com/61215550/181704951-488da75d-8c62-4191-81fb-bfc5d40db7e4.png)
- ![image](https://user-images.githubusercontent.com/61215550/181704970-c924b04e-1a6f-45a5-b904-ca4c3641ba46.png)
