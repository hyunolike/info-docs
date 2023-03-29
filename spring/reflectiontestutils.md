## 단위테스트 `ReflectionTestUtils`
> [참고자료](https://dncjf64.tistory.com/314)
- ✔ `private` 선언된 메소드, 변수 테스트 


```java
ReflectionTestUtils.setField({인스턴스}, {접근하려는 private 필드명}, {넣어줄 데이터 값});
ReflectionTestUtils.invokeMethod({인스턴스}, {호출하려는 private 메소드명}, {인자1}, {인자 2}, ...);
```


### 단점
- 접근하려는 메소드, 필드명 `String` 값으로 넘김
- compile time에 메소드명 오타 검증 불가

### 💡 `private` 필드, 메소드 테스트 하는 이유 
- [컨트롤러 단위테스트 쉽게](https://starplatina.tistory.com/entry/ReflectionTestUtils-%EB%A1%9C-%EC%BB%A8%ED%8A%B8%EB%A1%A4%EB%9F%AC-%ED%85%8C%EC%8A%A4%ED%8A%B8%EB%A5%BC-%EC%89%BD%EA%B2%8C)
