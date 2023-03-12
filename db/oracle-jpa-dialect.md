## Oracle - Spring Boot JPA | Dialect(방언)
> [참고자료](https://firework-ham.tistory.com/106)

### 🦁 방언 `Dialect`
- SQL >> 표준 ANCI SQL
- 🐶 `DBMS Vendor(공급업체)` 제공하는 sql 존재
  - MS SQL >> `T-SQL`
  - Oracle >> `PL/SQL` 
- 🧑🏻‍💻핵심
  - `ANCI SQL`: DBMS에서 공통적으로 사용 가능한 표준 SQL
  - `DBMS가 만든 언어`: 자신들만의 독자적인 기능을 추가하기 위해 만든 것으로 사용하는 DBMS에서만 사용 가능!
- 예시 (동일한 기능이자만 서로 다르게 제공)
  - MYSQL 에서 ID 값 증가 시키기 위해 auto increment 사용 가능
  - Oracle 에서는 이 기능 사용하지 않고 Sequence 사용해 기능 제공 

### 🦁 JPA는 기본적으로 직접 JDBC 레벨의 SQL 작성하지 않고 JPA가 직접 SQL 작성하고 실행
- Dialect 설정할 수 있는 추상화 방언 클래스를 제공하고 설정된 방언으로 각 DBMS에 맞는 구현체 제공
- 각 DBMS에 맞게 설정하자!


```yml
database-platform: org.hibernate.dialect.MariaDB103Dialect

database-platform: org.hibernate.dialect.Oracle10gDialect
```

### 🦁 하이버네이트 Dialect 설정과 종류
- Dialect 설정하기 위해선 hibernate 버전 먼저 확인 필요
  - `Spring Boot 2.2~` 방언 공식 자료 - [바로가기](https://docs.spring.io/spring-boot/docs/2.2.0.RELEASE/reference/html/appendix-dependency-versions.html)


Spring-Boot 2.2 버전부터는 hibernate 5.4.6.Final을 사용합니다.
https://docs.spring.io/spring-boot/docs/2.2.0.RELEASE/reference/html/appendix-dependency-versions.html

Dependency versions

The following table provides details of all of the dependency versions that are provided by Spring Boot in its CLI (Command Line Interface), Maven dependency management, and Gradle plugin. When you declare a dependency on one of these artifacts without dec

docs.spring.io

Spring-Boot 2.1을 사용한다면 방언은 아래를 참고하시면 됩니다.
https://docs.jboss.org/hibernate/orm/5.3/javadocs/org/hibernate/dialect/package-summary.html

org.hibernate.dialect (Hibernate JavaDocs)

Enum Summary  Enum Description Database List all supported relational database systems. ResultColumnReferenceStrategy Defines how we need to reference columns in the group-by, having, and order-by clauses. Package org.hibernate.dialect Description This pa

docs.jboss.org

Spring-Boot 2.2을 사용하신다면 아래를 참고하시면 됩니다.
https://docs.jboss.org/hibernate/orm/5.4/javadocs/org/hibernate/dialect/package-summary.html

org.hibernate.dialect (Hibernate JavaDocs)

Enum Summary  Enum Description Database List all supported relational database systems. ResultColumnReferenceStrategy Defines how we need to reference columns in the group-by, having, and order-by clauses. Package org.hibernate.dialect Description This pa

docs.jboss.org

TIP : Oracle 11g의 경우에는 Oracle 10g를 사용하면 됩니다.
