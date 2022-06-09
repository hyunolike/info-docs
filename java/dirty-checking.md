## 더티 채킹
- `Dirty`: 상태의 변화가 생긴 정도
- `Dirty Checking`: 상태 변경 검사

### 사용 예시
> JPA에서는 트랜잭션이 끝나는 시점에 변화가 있는 모든 엔티티 객체를 DB에 __자동으로 반영해줌!__
1. 트랜잭션 시작
2. 엔티티 조회
3. 엔티티 값 변경 ✔
4. 트랜잭션 커밋
- [결과] 데이터베이스 save 업데이트 진행 ⭐

### 개념
- 상태 변경 검사 >> `영속성 컨텐스트가 관리하는 엔티티` 에만 적용
  - detach된 엔티티(준영속)
  - db에 반영되기 전 처음 생성된 엔티티(비영속)
- 준영속, 비영속 모두 더티 채킹 대상에 포함하지 않음! >> 값을 변경해도 디비 업데이트 진행되지 않음

### 변경 부분만 업데이트 하고 싶을 때 - `@DynamicUpdate`
- 더티 채킹 >> 기본적으로 모든 필드 업데이트 진행
- JPA >> 전체 필드 업데이트하는 방식을 기본값

```java
@Getter
@NoArgsConstructor
@Entity
@DynamicUpdate // 변경한 필드만 대응 ⭐
public class Pay {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String tradeNo;
    private long amount;
```
