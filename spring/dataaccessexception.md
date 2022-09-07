## DataAccessException
> [참고자료](https://hyeonyeee.tistory.com/96)
### ✔(추가) unchecked exception / checked exception 
- `unchecked exception`: runtime exception 상속 ⭕
- `checked exception`: runtime exception 상속 ❌

### 1. SQLException
- JDBC >> 모든 Exception을 SQLException에 하나에 담아버림!
  - SQLException 복구 불가능
  - DAO 밖에서 SQLException 다룰 수 있는 가능성은 거의 없다.
  - ⭐가능한 빨리 언체크/런타임 예외로 전환해줘야 함

### 2. DataAccessException
- 스프링 DB관련 예외 >> `DataAccessException` 으로 한번 감싸줘서 알려줌
  - `dbms`에 따라 에러 코드 다르지만 >> 코드는 스프링에서 일관적으로 보여주니 일관성 있어서 좋다!! ㅋㅋㅋ
- jdbcTemplate >> SQLException을 단지 런타임 예외인 DataAccessException으로 포장하는 것이 아닌 db의 에러 코드를 DataAccessException 계층 구조의 클래스 중 하나로 매핑!
  - jdbcTemplate 던지는 예외 모두 >> DataAccessException의 서브클래스 
- driver / db meta info로 참고 >> db 종류 확인 >> db별로 미리 준비된 매핑 정보 참고해서 적절한 예외 클래스 선택!
  - db 달려져도 같은 종류의 에러라면 동일한 예외 받을 수 있음!
- 📌 주의 >> 키값 중복 되는 상황 --> 똑같은 예외 발생 x 
  - 데이터 엑세스 기술 상관없이 >> 키 값 중복되는 상황 >> 아래와 같이 동일한 예외 발생 x
  - JDBC >> `DuplicateKeyException` / 하이버네이트 >> `ContraintViolationException`
