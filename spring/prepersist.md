## `@Prepersist` feat 스프링 부트 @CreatedDate 직접 만들어 보기
> [참고 자료](https://bgpark.tistory.com/133)
- Entity가 영속성 컨테스트에 의해 저장되기 전에 `@Prepersist` 라는 콜백에 의해 객체에 직접 날짜를 입력하는 방법을 사용

### `@Prepersist`
- 해당 어노테이션이 정의된 메서드는 대상 Entity 데이터베이스에 저장되기전에 실행
- 이 메소드는 해당 엔티티에 현재 날짜 세팅
- 메소드 void 리턴

```java
@Prepersist
public void prePersist(){
  Date date = new Date();
  this.created = date;
  this.updated = created;
}
```
