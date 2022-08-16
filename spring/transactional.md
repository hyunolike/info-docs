## @Transactional
> [참고자료](https://bcp0109.tistory.com/322)
- 지정 가능 옵션
  - isolation
  - propagation
  - readOnly
  - rollbackFor
  - timeout

### 1. isolation
- 동시에 여러 사용자가 데이터 접근할 때 어디까지 허용할지 정하는 옵션
  - 트랜잭의 격리 수준 & 데이터의 일관성과 비례
- 5가지 옵션 제공
  - `READ_UNCOMMITTED`: 커밋되지 않은 데이터를 다른 트랜잭션에서 접근 가능 >> 존재하지 않는 데이터 읽는 현상 `Dirty Read`
  - `READ_COMMITED`: 트랜잭션은 커밋한 데이터만 읽을 수 있다.
  - `REPEATABLE_READ`: 하나의 트랜잭션은 하나의 스냅샷만 사용 가능
  - `SERIALIZABLE`: 가장 단순하고 엄격한 격리 수준 / 가장 안전하지만 성능 저하 ㅠ,ㅠ >> 극도의 안전성을 필요로 하지 않으면 자주 사용되지 않음
### 2. propagation 
- 
