## `Spring` `custom exception` 커스텀 예외처리
> [참고 자료](https://veneas.tistory.com/entry/Java-%EC%BB%A4%EC%8A%A4%ED%85%80-%EC%98%88%EC%99%B8-%EB%A7%8C%EB%93%A4%EA%B8%B0Custom-Exception)
> [참고 자료](https://bloowhale.tistory.com/72)

### 현재 예외 처리 트랜드
- `"Unchecked를 사용하여 예외들을 Custom Exception 클래스를 만들어 예외를 의도적으로 발생시켜 Custom Exception Class로 처리하는 것이 트렌드이다"`

|예외 종류|상속 받아야될 꺼|
|--------|------------------|
|일반 예외|`Exception` 상속받아 구현|
|실행 예외|`RuntimeException` 상속받아 구현|

- 사용자 정의 예외 클래스
  - 일반 예외: 컴파일러 체크❌
  - 실행 예외: 컴피알러 체크⭕
- 사용자 정의 예외 클래스 명 >> ...Exception 으로 끝나는 거 권장
  - 예시) `HyunhoException`
- 사용자 정의 예외 클래스 작성 시 생성자 2개 선언하는 것이 일반적
  - 매개 변수 없는 기본 생성자
  - 예외 발생 원인(예외 메시지) 전달하기 위해 String 타입의 매개변수 갖는 생성자
- 예외 메시지의 용도는 `catch()` 블록의 예외처리 코드 이용하기 위함


### `ExceptionHandler`
- 이건 서버의 잘못이 아닌 잘못된 요청이다라는 부분을 명시할 필요 
- `@Controller` `@RestController` 적용된 __Bean__ 내에서 발생하는 예외를 잡아서 하나의 메서드에서 처리해주는 기능
  - 즉, 컨트롤 단에서 발생하는 예외 잡아주고 개발자가 별도의 원하는 로직으로 변경할 수 있도록 해주는 친구
- 주의사항
  - controller, RestController에서만 사용
  - 리턴 타입 자유롭게 정의해서 사용
  - ExceptionHandler 등록한 Controller에서만 동작
  - 파라미터는 보통 Exception을 받지만 자유롭게 받을 수 있다.
- 반복되는 코드 단점 보완
  - `ControllerAdvice` `RestControllerAdvice`
  
