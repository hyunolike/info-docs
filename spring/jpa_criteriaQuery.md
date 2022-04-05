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
