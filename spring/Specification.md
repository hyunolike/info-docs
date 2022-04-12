## `Specification`
> [참고 자료](https://kohen.tistory.com/4)
> [참고 자료](https://javacan.tistory.com/entry/SpringDataJPA-Specifcation-Usage)


- ⭐ __검색조건__ 을 추상화한 객체 !!!
  - 검색 조건에 대해 `Specification`에 생성 >> 다양한 조건의 검색 수행 가능
- Spring Data >> Query Method만으로 모든 쿼리 커버 불가 ㅠ,ㅠ
  - Specification 이용해 조건쿼리 생성하는 방법이 있다!
- DB 쿼리의 조건을 스펙으로 작성해 Repository method에 적용하거나 몇가지 스펙을 조합해서 사용할 수 있게 도와줌

### 조건 검색 방법
1. Specification 입력 받도록 Repository 인터페이스 정의
2. 검색 조건을 모아 놓은 클래스 만들기(Specification 객체)
3. 검색 조건 조합한 Specification 인스턴스 이용해 __검색__ ✔

#### ✔ Specificaiton을 입력 받는 Repository 메서드 정의
```java
public interface ContentRepository extends Repository<Content, Long> {
	Page<Content> findAll(Specification<Content> spec, Pageable pageable); ✔ 
}
```

#### 2. 

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

  public static Specification<Order> isOrderStatus(final String memberName) { ⭐isOrderStatus()
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
  List<Order> result = OrderRepository.findAll(where(memberName(name)).and(isOrderStatus())); ⭐ memberName() isOrderStatus()
  return result;
}
```

#### 사용 예제
```java
public class ShippingBatchSpecification {

    public static Specification<BatchInfoEntity> batchCondition(BatchInfoEntity item){ 
        return new Specification<BatchInfoEntity>() {
            @Nullable
            @Override
            public Predicate toPredicate(Root<BatchInfoEntity> root, CriteriaQuery<?> criteriaQuery, CriteriaBuilder cb) {
                List<Predicate> predicates = new ArrayList<Predicate>();

                if(!StringUtils.isEmpty(item.getSvcId())){
                    predicates.add(cb.equal(root.get("productId"), item.getSvcId()));
                }else{
                    if(!item.getAspId().equals("ALL")){
                        predicates.add(cb.equal(root.get("aspId"), item.getAspId()));
                    }
                }

                if(!item.getTryReason().equals(TryReason.ALL)){
                    predicates.add(cb.equal(root.get("tryReason"), item.getTryReason()));
                }
                if(!item.getRequestor().equals(TryRequestor.ALL)){
                    predicates.add(cb.equal(root.get("requestor"), item.getRequestor()));
                }

                if(!StringUtils.isEmpty(item.getCardType())){
                    predicates.add(cb.equal(root.get("cardType"), item.getCardType()));
                }
              //  criteriaQuery.distinct(true);
                return cb.and(predicates.toArray(new Predicate[predicates.size()]));
            }
        };
    }
}
```

---
## 심화
### 단일 조건 조회
```java
private Specification<Member> getSigleSpec(Map<String, Object> map){
	return new Specification<Member>(){
		private static final long serialVersionUID = 1L;
		
		@Override
		public Predicate toPredicate(Root<Member> root, CriteriaQuery<?> query, CriteriaBuilder cb){
			Predicate p = cb.conjunction();
			if(map.get("id") != null) p = cb.and(cb.like(root.get("id"), "%"+(String) map.get("id")+"%")); ⭐ like 문
			if(map.get("name") != null) p = cb.and(cb.equal(root.get("useYn"), (String) map.get("userYn"))); ⭐ 동등 비교
			if(map.get("regDtm") != null) p = cb.and(
				cb.between(root.get("regDtm"), (String) map.get("regDtmSt"), (String) map.get("regDtmEd")) ⭐ between
			);
			return p;
		}
		};
	}
}
```
- `like`문: `like(컬럼(변수), "%"+조건값+"%")`
- 동등비교 경우: `equal(컬럼(변수), 조건값)`
- between 경우: `between(칼럼(변수), start, end)`
