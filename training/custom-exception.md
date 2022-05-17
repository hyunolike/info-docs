## 사용자 정의 예외 처리 실습
- 필요 클래스
  - `CustomException.class`
  - `CustomExceptionCode.enum`
  - `ExceptionToString.class` - 문자 변환 기능 클래스
  - `CustomExceptionTest.class` - 실행 클래스
- ![image](https://user-images.githubusercontent.com/61215550/168708104-97302434-812f-4ef7-9d52-7523a700b49b.png)

### `CustomException.class`
```java
class CustomException extends RuntimeException{
  ...
}
```

### `CustomExceptionCode.enum`
```java
enum CustomExceptionCode{
  ERROR_CODE(400, "에러 코드 이유", "에러 코드 메시지");
  
  @Getter
  private int code;
  @Getter
  private String reason;
  @Getter
  private String message;
  
  생성자...
}
```

## 예외 처리
- 예외 발생시키기
  - `Exception e = new Exception("고의로 예외 발생");`
  - `throw e;`
