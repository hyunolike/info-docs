## mariadb `Sequence` 
> [참고 자료](https://mariadb.com/kb/ko/sequence-overview/)
- 시퀀스: 지정된 대로 일련의 숫자값을 생성하는 객체
- 값을 캐싱 >> `AUTO INCREMENT` 보다 빠르다

### 1. 시퀀스 생성
```SQL
CREATE SEQUENCE s START WITH 100 INCREMENT BY 10;
```

### 2. 시퀀스 객체 사용
```SQL
NEXT VALUE FOR sequence_name
NEXTVAL(sequence_name)

LASTVAL(sequence_name) # 시퀀스 마지막 값 얻어오기
```

### 3. 시퀀스 제거
```sql
DROP SEQUENCE s;
```
