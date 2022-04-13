## `JPQL` (Java Persistence Query Language)
> [참고 자료](https://data-make.tistory.com/614)

- 테이블아닌 ✔ __엔티티 객체__ 대상으로 검색하는 객체지향 쿼리 
- SQL을 추상화해서 특정 데이터베이스 SQL에 의존하지 않음
- JPA >> JPQL 분석 >> 적절한 SQL 만들어 데이터베이스 조회
- 방언(Dialect)만 변경하면 JPQL을 수정하지 않고 자연스럽게 데이터베이스 변경 가능

### `fetch join`
- `JPQL` 에서 __성능 최적화__ 위해 제공하는 기능
- 연관된 엔티티나 컬렉션을 한 번에 같이 조회(JPQL은 결과를 반환할 때 연관관계까지 고려하지 않음 -> `fetch join`)
