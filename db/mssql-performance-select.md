## MSSQL DB 성능 향상
> [참고 자료](https://kwomy.tistory.com/37)
### 1. 생성
- DB 생성 시
  - 명칭은 해당  서비스 파악 가능하도록 명명
- USER 생성 시
  - USER ID >> 유관 서비스 파악 가능하도록 명명
  - Password >> 운용팀 DBA 생성 규칙 따름
- TABLE 생성 시
  - `TABLE 길이` + `COLOUMN 길이` >> 8K 넘지 않도록
  - 이름은 일관성 있게 >> EX. TBL_OOO, TN_OOO
  - PK / FK Column 고정길이 형식 사용 >> EX. CHAR TYPE
  - Trigger 사용 자제
  - table 소유자는 항상 dbo가 되도록!!!
- DATA TYPE 정의 시
  - 데이터 타입 중 항상 가장 작은 데이터타입 선택
  - 텍스트 데이터 길이 매우 가변젹 >> VARCHAR 타입 사용하는 것이 좋다
  - 16비트문자 데이터 저장할 거 아니면 >> NVARCHAR, NCHAR 데이터 타입 사용하지 말자
  - 긴 문자열 저장할 때, 문자열 길이 8000자 이하 >> TEXT 대신 VARCHAR 데이터타입 사용!!
  - 숫자만 저장하는 칼럼 >> INTEGER와 같은 숫자데이터 타입 사용
- 인덱스 생성 시
  - WHERE 절 많이 사용하는 경우 사용
  - Covered Index인 경우 선택도가 좋은 조건부터 순서대로 생성
  - 구간별 선택이 많은 칼럼 >> 클러스터 인덱스 추천
  - PK 정의 시 >> non-Cluster index 정의하되 구간별 선택이 많은 칼럼인 경우 클러스터 인덱스 생성
### 2. 쿼리 작성 
- 테이블의 모든 칼럼이 아닌 __필요 칼럼의 레코드__ 만 반환 ✔
  - `select *` 사용하는 것은 피하기
  - 사용하지 않는 데이터 호출하는 것만으로 많은 부하 발생 >> `@Query(value = "SELECT t FROM Table t WHERE t.name = :NAME AND u.age = :AGE")` << 객체 전체 호출시는 ???
  - 특히 text 타입 데이터 호출시에 그 정도 심함 
  - data type의 byte가 적은 column 주로 사용하는 것이 좋음 
- 테이블 전체 row 수 알고 싶으면 `sys.sysindexes table의 row 칼럼` 사용
  - count 호출 >> null 값 제외한 count 가져옴
  - null값 일일이 체크 시 호출 속도 저하 ㅠ,ㅠ >> null 체크하는 경우가 아닌 대부분 경우 `count(*)` 사용
  - `count(*)` >> null 값 경우도 모두 count 추가 >> 성능 저하 많이 개선
  - ✔ `SELECT COUNT(*)` >> 테이블 스캔해서 ROW 수 반환 >> 큰 테이블에서 시간 많이 소요 >> 이 경우 `sysindexes` 시스템 테이블 사용 >> 테이블의 칼럼은 각 row 수를 값으로 가짐
```sql
-- 잘못된 예
SELECT count(f_nickname) FROM tbl_member 
SELECT count(*) FROM tbl_member

-- 올바른 예
 SELECT f_nickname FROM sys.sysindexes WHERE id  OBJECT_ID('tbl_member') AND indid < 2; ✔
```
...
---
## 참고 자료 
- [jpa 부하테스트](https://velog.io/@qf9ar8nv/JPA-N1-%EB%AC%B8%EC%A0%9C-%EA%B7%B8%EB%A6%AC%EA%B3%A0)
