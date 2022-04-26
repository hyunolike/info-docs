## 기본 타입 vs 박싱된 기본타입
> [참고 자료](https://kounjeong.tistory.com/21)

- 기본타입: `int` `long` `double` `boolean` `char` 등
- 박싱된 기본타입(참조타입): `Integer` `Long` `Double` `Boolean` `Character` 등

### 박싱, 언박싱
- 박싱: int >> Integer
- 언박싱: Integer >> int
- 차이점 ✔
  - 식별성
  - null
  - 제네릭 타입 사용가능 (참조 타입)

### 원시 타입 장점
- 접근 속도

### 결론
- 성능과 메모리에 장점이 있는 원시 타입 먼저 고려하기!! ✔
- 기본적으로 순수 기본타입을 사용하자?
  - 비즈니스 로직상 null 발생할 수 있다. 그럴땐 박싱된 참조 타입 사용! >> 그래도 사용하지 말자ㅠ,ㅠ 
  - 이유는 박싱된 intValue(); 할 때 null이면 장애나고 int로 값을 꺼낼 때나 Integer에 값을 저장할 때 다 __속도 저하__ 발생 ㅠ,ㅠ ⭐⭐

