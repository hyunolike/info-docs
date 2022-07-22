## `JPA` 벌크 연산
> [참고자료](https://dev-coco.tistory.com/169)

### 1. 벌크 연산
- `UPDATE` `DELETE` 문 지원 / `Hibernate` >> `INSERT`문도 지원
- `executeUpdate()` 메서드 통해 벌크 연산 수행
- ⭐벌크연산은 __영속성 컨텍스트 무시하고 DB에 직접 쿼리 한다는 점__ 주의
  - DB에 반영된 결과 >> 영속성 컨텍스트에는 반영 X
```java
String sql = 
    "update Member m" +
    "set m.salary = m.salary * 1.1" +
    "where m.salary < :salary";
 
int resultCount = em.createQuery(sql)
                    .setParameter("salary", 30000000)
                    .executeUpdate();
                    
String sql = 
    "delete from Member m" +
    "where m.age > :age";
 
int resultCount = em.createQuery(sql)
                    .setParameter("age", 70)
                    .executeUpdate();
```

### 2. 요약 ✔
- JPA >> (단건) >> `Dirty Checking` 통해 `UPDATE` 수행
- JPA >> (여러건) >> `Bulk Operation` 통해 한번에 수정하거나 삭제
