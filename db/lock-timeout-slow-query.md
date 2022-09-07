## MySQL Lock wait timeout exceed
> [참고자료](https://brunch.co.kr/@purpledev/4)
- 항상 발생하는 문제는 아니고 가끔 발생 ㅠ,ㅠ

### 1. 트랜잭션 수행 시간이 길다 ...
- 일반적으로 `Lock timeout` 발생 이유 >> 단일 트랜잭션 수행 시간이 긴 경우 발생
  - 배치성 작업 >> 트랜잭션 수행 시간 특히 주의 ...ㅎ

#### 1.1 innodb lock wait timeout 값 작게 설정한 경우
```sql
SELECT @@innodb_lock_wait_timeout; -- 설정된 값 확인

SET GLOBAL innodb_lock_wait_timeout = 20; -- 설정 값 수정
```

### 2. Isolation level과 관련
- RDBMS 의 Isolation level과 관련 >> SELECT 문의 실행 시간이 오래 걸리는 경우 >> `timeout exceeded` 발생 ㅠ,ㅠ
  - `READ COMMITED`
  - `REPEATABLE READ`
- `READ COMMITED`
  - commit 된 데이터만 읽는 것을 허용하는 레벨
  - 읽기의 경우: select 문 수행되는 동안 해당 데이터에 Shared lock 걸리고, select가 완료되면 lock 해제되는 것
  - 쓰기의 경우: 데이터를 변경하는 동안 다른 트랜잭션은 해당 데이터를 변경할 수 없고 wait하는 것
  - ⭐정리: 읽기는 select / 쓰기는 트랜잭션 단위 >> lock 발생!! 
  - ✔ Oracle의 Default level !!
- `REPEATABLE READ`
  - select에서 해당 데이터 Shared lock 걸고 데이터의 Snapshot 생성>> 이후, 동일 트랜잭션 내의 select는 snapshot에서 읽기
  - ✔ MySQL의 Default level !!
  
