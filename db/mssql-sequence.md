## `MSSQL` SEQUENCE
> [공식 문서](https://docs.microsoft.com/ko-kr/sql/t-sql/statements/create-sequence-transact-sql?view=sql-server-ver16)
- 실무에서 자주 사용

```SQL
CREATE SEQUENCE [schema_name . ] sequence_name  
    [ AS [ built_in_integer_type | user-defined_integer_type ] ]  
    [ START WITH <constant> ]  
    [ INCREMENT BY <constant> ]  
    [ { MINVALUE [ <constant> ] } | { NO MINVALUE } ]  
    [ { MAXVALUE [ <constant> ] } | { NO MAXVALUE } ]  
    [ CYCLE | { NO CYCLE } ]  
    [ { CACHE [ <constant> ] } | { NO CACHE } ]  
    [ ; ]  
```

### 인수
- CYCLE | NO CYCLE
  - 새 시퀀스 개체의 기본 순환 옵션 >> `NO CYCLE`
  - 시작 값이 아니라 최솟값 또는 최댓값에서 다시 시작
- CACHE | <constant> | NO CYCLE
  - 기본값 >> CACHE

---
## ✔ 추가
- 시퀀스 >> 사용자 별 권한을 사용 여부 나뉘게됨
- 아래는 시퀀스 권한 확인 쿼리
    

```sql
GRANT CREATE SEQUENCE ON SCHEMA::seq TO SequenceCreator  
GO
```

### 1. 시퀀스 다시 시작
```SQL
ALTER SEQUENCE Test.CountBy1 RESTART WITH 1 ;  -- 시퀀스 초기화
SELECT NEXT VALUE FOR Test.CountBy1; -- 시퀀스 증가
```
    
### 2. 시퀀스 변경
```SQL
ALTER SEQUENCE Test. TestSeq  
    RESTART WITH 100  
    INCREMENT BY 50  
    MINVALUE 50  
    MAXVALUE 200  
    NO CYCLE  
    NO CACHE  
;  
GO  
```
    
   
