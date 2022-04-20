## mssql 암호화 연결
> [참고 자료](https://docs.microsoft.com/ko-kr/sql/connect/jdbc/connecting-with-ssl-encryption?view=sql-server-ver15)
- __Java 애플리케이션__ 에서 `TLS(전송 계층 보안)` 암호화를 사용할 수 있도록 하는 연결 문자열 속성을 사용? 해야 된다! ✔

### 암호화 사용하여 연결
- `encrypt=true`
- `trustServerCertificate=true`
- 위에 2가지 설정을 하면 `SQL Server TLS` 인증서의 유효성을 검사하지 않음 

```java
String connectionUrl =
    "jdbc:sqlserver://localhost:1433;" +
     "databaseName=AdventureWorks;integratedSecurity=true;" +
     "encrypt=true;trustServerCertificate=true";
```

### 스프링에서는 ???
```yml
spring:
  datasource: 
    url: jdbc:sqlserver://localhost:1433;DatabaseName=udm;integratedSecurity=true;encrypt=true;trustServerCertificate=true ⭐
    driver-class-name: com.microsoft.sqlserver.jdbc.SQLServerDriver
    username: root
    password: mona!234
    initialization-mode: never
```

## `TLS` 전송 보안 계층 (Transport Layer Security)
> [참고 자료](https://jundol.me/146)

- 암호화 보안 프로토콜
  - 두 당사자가 개인정보 보호 및 데이터 무결성으로 통신하도록 하여 안전한 연결 제공
- 기존 SSL 프로토콜에서 발전한 것
  - 처음 네스케이프에 의해 발명된 SSL이 표준화가 되면 바뀐 이름이 `TLS` ✔
  - TLS 1.0은 `SSL 3.0` 계승 한 것
- 기밀성, 데이터 무결성, 인증, 디지털 인증서 사용하는 인증을 제공하는 것
