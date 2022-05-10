## `spring boot` + `mssql` >> 도커 컴포즈로 띄우기
### 1. 구조
![image](https://user-images.githubusercontent.com/61215550/167562922-98ed7a5f-091b-413a-bdc7-52fad874a800.png)

### 2. 주의 사항
![image](https://user-images.githubusercontent.com/61215550/167562988-d64cad1d-5837-4aea-a676-ec4436905638.png)

### 3. 주요 코드
- 도커 컴포즈 실행
  - `docker-compose -f ./docker-compose/docker-compose_server.yml -f ./docker-compose/docker-compse_mssql.yml -f ./docker-compose/docker-compose_sftp.yml up`
- `docker-compose_server.yml`
```yml
version: "3.8"
services:
  spring-server:
    image: openjdk:8-jre
    ports:
      - "8888:8181"
    container_name: spring_server
    volumes:
      - ../build/libs:/app
    entrypoint: ["java", "-jar", "/app/spring-docker-0.0.1-SNAPSHOT.jar"]
    depends_on:
      - mssql_db
    links:
      - mssql_db
    networks:
      - test-network


networks:
  test-network:
```

- `docker-compose_mssql.yml`
```yml
version: "3.8"
services:
  mssql_db :
    image: mcr.microsoft.com/mssql/server:2017-latest
    container_name: mssql_db
    hostname: mssql_db ⭐
    ports:
      - "1433:1433"
    expose:
      - "1433"
    volumes:
      - volume-server:/var/opt/mssql/
    environment:
      ACCEPT_EULA: Y
      SA_PASSWORD: your@Password
    networks:
      - test-network


networks:
  test-network:
volumes:
  volume-server:
```

- `application.yml`
```yml
# 공통 설정
server:
  port: 8181

spring:
  datasource:
    url: jdbc:sqlserver://mssql_db:1433;DatabaseName=UDM;encrypt=true;trustServerCertificate=true ⭐ 컴포즈 설정 파일의 hostname과 일치!
    driver-class-name: com.microsoft.sqlserver.jdbc.SQLServerDriver
    username: sa
    password: your@Password
    initialization-mode: never
  jpa:
    hibernate:
      ddl-auto: none
    database: sql-server
    generate-ddl: false
    open-in-view: false
    #    show-sql: true
    properties:
      hibernate.proc.param_null_passing: true
      javax.persistence.query.timeout: 10000
      hibernate.dialect: org.hibernate.dialect.SQLServer2008Dialect
      hibernate.format_sql: true
```
