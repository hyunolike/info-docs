## `test` Mockito
> [참고자료](https://unluckyjung.github.io/testcode/2021/11/29/Mokito-Basic/)
- Mockito - [참고자료](https://velog.io/@max9106/Mockito-Mockito%EB%9E%80)
  - 진짜 객체처럼 동작하지만 프로그래미가 직접 컨트롤 할 수 있는 객체
  - 구현체가 아직 없는 경우
  - Mock 객체 만들고 관리하고 검증 할 수 있는 방법 제공(가짜 객체)
### 💡 Mock 객체 행동 관리 
- void 메소드는 아무런 일도 발생 x
- return 값이 있는 메소드는 `null`
- Primitive 타입의 변수가 있는 경우 기본 값
- 콜렉션은 비어있는 콜렉션 만들어줌
### 💡 Mock 객체 생성 이후 테스트 할 행동 (가정)
- 특정한 매개변수 >> 특정한 값 리턴 및 예외 호출
- void 메소드 호출 시 예외 던질 수 있음
- 동일한 메소드가 여러번 호출 시 각각 다르게 행동 가능
### `@ExtenWith(MockitoExtension.class)`
- `init` `open` 메소드 호출 생략

### `@Mock` 
- mock 객체 생성

### `@InjectMocks`
- ⭐ 보통 `DAO` `Service` 목객체 주입

