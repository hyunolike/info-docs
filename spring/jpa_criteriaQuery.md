- [참고자료](https://happygrammer.tistory.com/149)
## `CriteriaQuery`
- `JPQL` > 자바코드로 바꿔준다!
- 문자가 아닌 코드로 작성함으로 문법 오류를 컴파일 단계에서 잡아줌

```java
CriteriaBuilder builder = em.getCriteriaBuilder();
CriteriaQuery<MemberJPQL> query = builder.createQuery(MemberJPQL.class);

✔ 조회의 시작점을 뜻한다 >> Root 객체
Root<MemberJPQL> m = query.from(MemberJPQL.class);
query.select(m).distinct(true); 

TypedQuery<MemberJPQL> typeQuery = em.createQuery(query);
List<MemberJPQL> members = typeQuery.getResultList();
```

### Criteria 이용한 질의
- 자바 코드 이용해 `JPQL` 작성할 수 있게 도와주는 타입 세이트 제공하는 쿼리
- 네이티브 SQL 쿼리 대체해 `HQL` `JPQL` 자바 코드 이용해 작성할 수 있게 해줌. 

--- 
### JPA 질의 방법 종류 ✔ 
- `Criteria`
- `QueryDSL`
- `Native SQL`

#### `JPQL`을 `Criteria` 변환
`기존`
```java
SELECT c FROM COUNTRY c WHERE c.population > :p
```


`변환`
```java
CriteriaQuery<Country> q = cb.createQuery(Country.class);
Root<Country> c = q.from(Country.class);
q.select(c);
ParameterExpression<Integer> p = cb.parameter(Integer.class);
q.where(cb.gt(c.get("population"), p));
```
