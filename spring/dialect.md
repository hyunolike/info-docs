## Dialect 방언
> [참고자료](https://firework-ham.tistory.com/106) <br>
> [공식문서](https://docs.jboss.org/hibernate/orm/5.3/javadocs/org/hibernate/dialect/package-summary.html)
- SQL 표준 >> `ANCI SQL`
- DBMS Vendor(공급업체) >> My-SQL, MS-SQL, Oracle, Postgre SQL >> 제공하는 SQL 존재
  - MS-SQL(T-SQL) / Oracle(PL/SQL)
- ✔DBMS에서 만든 SQL >> 자신들만의 독자적인 기능 추가 하기 위해 만든 것이기에 사용하는 DBMS에서만 사용 가능

### 1. 방언이란
- JPA >> 직접 SQL 작성하고 실행
  - 해당 DBMS에 맞춰 SQL 생성 >> 어떤 종류인지 알지 못하면 문제 발생 ㅠ,ㅠ 

```yml
# Maria DB
database-platform: org.hibernate.dialect.MariaDB103Dialect

# Oracle
database-platform: org.hibernate.dialect.Oracle10gDialect
```


- ⭐주의사항
  - Spring Boot 버전마다 사용하는 hibernate 버전 다름 ㅠ,ㅠ
