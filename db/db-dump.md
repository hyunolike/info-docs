## DB Dump `추가 2023/02/22`
### MySQL dump / import 디비 덤프 및 임포트
> [참고자료](https://cheershennah.tistory.com/173)
#### 1. Dump
##### 1-1. 전체 스키마
```sql
$> mysqldump -u[사용자아이디] -p[패스워드] 데이터베이스명 > 경로 및 저장될 파일명.sql

// ex) mysqldump -uroot -p1234 testdb > /root/backup/testdb.sql
```
##### 1-2. 특정 테이블
```sql
$> mysqldump -u[사용자아이디] -p[패스워드] 데이터베이스명 테이블명 > 경로 및 저장될 파일명.sql

// ex) mysqldump -uroot -p1234 testdb testtb > /root/backup/testdb_testtb.sql
```
#### 2. Import 
##### 2-1. 전체 스키마
> ⭐ 미리 가져올 데이터베이스 생성해야 됨!
```sql
$> mysql -u[사용자아이디] -p[패스워드] 데이터베이스명 < 경로 및 덤프 파일명.sql

// ex) mysql -uroot -p1234 testdb < /root/backup/testdb.sql
```
##### 2-2. 특정 테이블 
```sql
$> mysql -u[사용자아이디] -p[패스워드] -데이터베이스명=테이블명 < 경로 및 저장될 파일명.sql

// ex) mysql -uroot -p1234 -testdb=testtb < /root/backup/testdb_testtb.sql
```

---
> [참고자료](https://velog.io/@pomeranian91/DB-dump%EC%9D%98-%EA%B0%9C%EB%85%90-%EB%B0%8F-%EB%B0%B1%EC%97%85%EB%B3%B5%EA%B5%AC-%EB%B0%A9%EB%B2%95)
- 대상 데이터 `INSERT QUERY` 바꿔서 저장하는 방법
- ✔ DB 상태 저장 및 불러오는 기능 가진 툴
- `INSERT` 문 치환되기 때문에 DBMS / 기타 버전문제에 크게 영향 받지 않음

### 로드 방법
- `DB` SQL 파일 저장
