## jpa에서 Query 사용하는 방법
- 크게 2가지 존재
  - `JPQL` 사용하는 JPQL 쿼리
  - `SQL` 쿼리 사용하는 방법

### `SQL` 쿼리 사용 예시
```JAVA
Query query = em.createNativeQuery("select * from u where u.id = ?"); // 쿼리 입력
return query = query.getSingleResult(); // 데이터 취득 
```
