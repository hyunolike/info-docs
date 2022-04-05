## `Specification`
- Spring Data >> Query Method만으로 모든 쿼리 커버 불가 ㅠ,ㅠ
  - Specification 이용해 조건쿼리 생성하는 방법이 있다!
- DB 쿼리의 조건을 스펙으로 작성해 Repository method에 적용하거나 몇가지 스펙을 조합해서 사용할 수 있게 도와줌


### 사용 방법
#### 1. 명세 기능 사용하기!
- `JpaSpecificationExecuter` 인터페이스 상속

```java
public interface OrderRepository extends JpaRepository<Order, Long>, JpaSpecificationExecuter<Order> {

}
```

#### 2. 명세 정의
- `toPredicate()`메소드 구현

```java
public class OrderSpecification {
  public static Specification<Order> memberName(final String memberName) { ⭐memberName()
    return new Specification<Order>() {
      public Predicate toPredicate(Root<Order> root, CriteriaQuery<?> query, CriteriaBuilder builder) {
        if(StringUtils.isEmpty(memberName)) return null;

        Join<Order, Member> m = root.join("member", JoinType.INNER);

        return builder.equal(m.get("name"), memberName);
      }
    }
  }

  public static Specification<Order> isOrderStatus(final String memberName) {
    return new Specification<Order>() {
      public Predicate toPredicate(Root<Order> root, CriteriaQuery<?> query, CriteriaBuilder builder) {
        return builder.equal(root.get("status"), OrderStatus.ORDER);
      }
    };
  }
}
```

#### 2-1. 명세 사용하기
```java
public List<Order> findOrders(String name) {
  List<Order> result = OrderRepository.findAll(where(memberName(name)).and(isOrderStatus())); ⭐ memberName()
  return result;
}
```

