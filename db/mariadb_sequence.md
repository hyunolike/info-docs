## mariadb `Sequence` 
> [참고 자료](https://mariadb.com/kb/ko/sequence-overview/)
- 시퀀스: 지정된 대로 일련의 숫자값을 생성하는 객체
- 값을 캐싱 >> `AUTO INCREMENT` 보다 빠르다
- `SELECT * FROM user_sequence` >> 시퀀스 조회

### 1. 시퀀스 생성
```SQL
CREATE SEQUENCE s START WITH 100 INCREMENT BY 10;
```
- `INCREMENT BY 1` : 증감수 1. default 1
- `START WITH 1` : 시작수 1
- `MINVALUE 1` : 최소값 1
- `MAXVALUE 999999` : 최대값 999999
- `NOCYCLE` 
  - `CYCLE` : 최대값 후 다시 최소값부터 시작
  - `NOCYCLE` : 최대값 후 사용 중지
- `CACHE` 
  - `CACHE` : 설정 시 메모리에 미리할당
  - `NOCACHE` : 할당 X


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
