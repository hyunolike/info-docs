## `Exception` 전략
> [참고 자료](https://cheese10yun.github.io/spring-guide-exception/)

### 통일된 Error Response 객체
- 항상 동일한 에러 응답 가져야 함 >> 이를 어길시 클라이언트에서 예외 처리를 항상 동일한 로직으로 처리 불가 ㅠ,ㅠ
- `Map<Key, Value>` 형식 좋지 않다고 생각(주관적) >> __런타임__ 시 정확한 형태 갖추기에 객체 처리하는 개발자는 무슨 키에 무슨 데이터 있는지 확인하기 어려움!

```java
@ExceptionHandler(MethodArgumentNotValidException.class)
protected ResponseEntity<ErrorResponse> handleMethodArgumentNotValidException(MethodArgumentNotValidException e) {
    log.error("handleMethodArgumentNotValidException", e);
    final ErrorResponse response = ErrorResponse.of(ErrorCode.INVALID_INPUT_VALUE, e.getBindingResult());
    return new ResponseEntity<>(response, HttpStatus.BAD_REQUEST);
}
```
- ⭐ 리턴 타입 `ResponseEntity<ErrorResponse>` 이렇게 명확히 추론 가능하도록 쉽게 구성 바람직

### Error Response JSON
```java
{
  "message": " Invalid Input Value",
  "status": 400,
  // "errors":[], 비어있을 경우 null 이 아닌 빈 배열을 응답한다.
  "errors": [
    {
      "field": "name.last",
      "value": "",
      "reason": "must not be empty"
    },
    {
      "field": "name.first",
      "value": "",
      "reason": "must not be empty"
    }
  ],
  "code": "C001"
}
```

- message : 에러에 대한 message를 작성합니다.
- status : http status code를 작성합니다. header 정보에도 포함된 정보이니 굳이 추가하지 않아도 됩니다.
- errors : 요청 값에 대한 field, value, reason 작성합니다. 일반적으로 @Valid 어노테이션으로 JSR 303: Bean Validation에 대한 검증을 진행 합니다.
  - 만약 errors에 바인인된 결과가 없을 경우 null이 아니라 빈 배열 []을 응답해줍니다. null 객체는 절대 리턴하지 않습니다. null이 의미하는 것이 애매합니다.
- code : 에러에 할당되는 유니크한 코드값입니다.

### Error Response 객체
```java
@Getter
@NoArgsConstructor(access = AccessLevel.PROTECTED)
public class ErrorResponse {

    private String message;
    private int status;
    private List<FieldError> errors;
    private String code;
    ...

    @Getter
    @NoArgsConstructor(access = AccessLevel.PROTECTED)
    public static class FieldError {
        private String field;
        private String value;
        private String reason;
        ...
    }
}
```
- ⭐POJO 객체로 관리 시 `errorResponse.getXXX();` 명확하게 객체에 있는 값을 가져올 수 있음
- 특정 예외에 대해서 `ErrorResponse` 객체를 어떻게 만들 것인가에 대한 책임 명확하게 갖는 구조로 설계 가능

### `@ControllerAdvice`로 모든 예외 핸들링
- 모든 예외 한 곳에서 처리 가능
- 해당 코드의 세부적인 것은 중요하지 않으며 가장 기본적이며 필수적으로 처리하는 코드

```java
@ControllerAdvice
@Slf4j
public class GlobalExceptionHandler {

    /**
     *  javax.validation.Valid or @Validated 으로 binding error 발생시 발생한다.
     *  HttpMessageConverter 에서 등록한 HttpMessageConverter binding 못할경우 발생
     *  주로 @RequestBody, @RequestPart 어노테이션에서 발생
     */
    @ExceptionHandler(MethodArgumentNotValidException.class)
    protected ResponseEntity<ErrorResponse> handleMethodArgumentNotValidException(MethodArgumentNotValidException e) {
        log.error("handleMethodArgumentNotValidException", e);
        final ErrorResponse response = ErrorResponse.of(ErrorCode.INVALID_INPUT_VALUE, e.getBindingResult());
        return new ResponseEntity<>(response, HttpStatus.BAD_REQUEST);
    }

    /**
     * @ModelAttribut 으로 binding error 발생시 BindException 발생한다.
     * ref https://docs.spring.io/spring/docs/current/spring-framework-reference/web.html#mvc-ann-modelattrib-method-args
     */
    @ExceptionHandler(BindException.class)
    protected ResponseEntity<ErrorResponse> handleBindException(BindException e) {
        log.error("handleBindException", e);
        final ErrorResponse response = ErrorResponse.of(ErrorCode.INVALID_INPUT_VALUE, e.getBindingResult());
        return new ResponseEntity<>(response, HttpStatus.BAD_REQUEST);
    }

    /**
     * enum type 일치하지 않아 binding 못할 경우 발생
     * 주로 @RequestParam enum으로 binding 못했을 경우 발생
     */
    @ExceptionHandler(MethodArgumentTypeMismatchException.class)
    protected ResponseEntity<ErrorResponse> handleMethodArgumentTypeMismatchException(MethodArgumentTypeMismatchException e) {
        log.error("handleMethodArgumentTypeMismatchException", e);
        final ErrorResponse response = ErrorResponse.of(e);
        return new ResponseEntity<>(response, HttpStatus.BAD_REQUEST);
    }

    /**
     * 지원하지 않은 HTTP method 호출 할 경우 발생
     */
    @ExceptionHandler(HttpRequestMethodNotSupportedException.class)
    protected ResponseEntity<ErrorResponse> handleHttpRequestMethodNotSupportedException(HttpRequestMethodNotSupportedException e) {
        log.error("handleHttpRequestMethodNotSupportedException", e);
        final ErrorResponse response = ErrorResponse.of(ErrorCode.METHOD_NOT_ALLOWED);
        return new ResponseEntity<>(response, HttpStatus.METHOD_NOT_ALLOWED);
    }

    /**
     * Authentication 객체가 필요한 권한을 보유하지 않은 경우 발생합
     */
    @ExceptionHandler(AccessDeniedException.class)
    protected ResponseEntity<ErrorResponse> handleAccessDeniedException(AccessDeniedException e) {
        log.error("handleAccessDeniedException", e);
        final ErrorResponse response = ErrorResponse.of(ErrorCode.HANDLE_ACCESS_DENIED);
        return new ResponseEntity<>(response, HttpStatus.valueOf(ErrorCode.HANDLE_ACCESS_DENIED.getStatus()));
    }

    @ExceptionHandler(BusinessException.class)
    protected ResponseEntity<ErrorResponse> handleBusinessException(final BusinessException e) {
        log.error("handleEntityNotFoundException", e);
        final ErrorCode errorCode = e.getErrorCode();
        final ErrorResponse response = ErrorResponse.of(errorCode);
        return new ResponseEntity<>(response, HttpStatus.valueOf(errorCode.getStatus()));
    }


    @ExceptionHandler(Exception.class)
    protected ResponseEntity<ErrorResponse> handleException(Exception e) {
        log.error("handleEntityNotFoundException", e);
        final ErrorResponse response = ErrorResponse.of(ErrorCode.INTERNAL_SERVER_ERROR);
        return new ResponseEntity<>(response, HttpStatus.INTERNAL_SERVER_ERROR);
    }
}
```

### Error Code 정의
```java
public enum ErrorCode {

    // Common
    INVALID_INPUT_VALUE(400, "C001", " Invalid Input Value"),
    METHOD_NOT_ALLOWED(405, "C002", " Invalid Input Value"),
    ....
    HANDLE_ACCESS_DENIED(403, "C006", "Access is Denied"),

    // Member
    EMAIL_DUPLICATION(400, "M001", "Email is Duplication"),
    LOGIN_INPUT_INVALID(400, "M002", "Login input is invalid"),

    ;
    private final String code;
    private final String message;
    private int status;

    ErrorCode(final int status, final String code, final String message) {
        this.status = status;
        this.message = message;
        this.code = code;
    }
}
```
- 에러 코드는 `enum` 타입으로 한 곳에서 관리
- 에러 코드 전체적으로 흩어져있을 경우 코드, 메시지의 중복을 방지하기 어렵고 전체적으로 관리하는 것이 어려움
- 에러 메시지 >> common과 같이 각 도메인별로 관리하는 것이 효율적

### Business Exception 처리
- Business Exception: 요구사항에 맞지 않을 경우 발생시키는 Exception 처리
  - 요구사항에 맞게 직접 Exception을 발생시키는 것들을 말함
- ⭐ 유지 보수하기 좋은 코드를 만들기 위해서는 Exception을 발생 시켜야 됨.
  - 쿠폰을 입력해서 상품을 주문했을 경우 상품 계산 로직에서 이미 사용해 버린 쿠폰이면 로직을 이어가기 어렵...
  - ✔ 단순히 어려운 것이 아닌 해당 계산 로직의 책임이 증가
  - 객체의 적절한 책임을 주기 위해서 / 본인이 처리 못하는 상황일 경우 >> 적절한 Exception 발생
- ⭐ 클린코드 >> 오류 코드보다 예외를 사용!!

```java
public class DeviceController {
    ...
    public void sendShutDown() {
        DeviceHandle handle = getHandle(DEV1);
        // 디바이스 상태를 점검한다.
        if (handle != DeviceHandle.INVALID) {
            // 레코드 필드에 디바이스 상태를 저장한다.
            retrieveDeviceRecord(handle);
            // 디바이스가 일시정지 상태가 아니라면 종료한다.
            if (record.getStatus() != DEVICE_SUSPENDED) {
                pauseDevice(handle);
                clearDeviceWorkQueue(handle);
                closeDevice(handle);
            } else {
                logger.log("Device suspended. Unable to shut down");
            }
        } else {
            logger.log("Invalid handle for: " + DEV1.toString());
        }
    }
    ...
}
```
- 😂 `if-else`문의 반복으로 비즈니스 코드를 이해하기 어렵다 

```java
public class DeviceController {
    ...
    public void sendShutDown() {
        try {
            tryToShutDown();
        } catch (DeviceShutDownError e) {
            logger.log(e);
        }
    }

    private void tryToShutDown() throws DeviceShutDownError {
        DeviceHandle handle = getHandle(DEV1);
        DeviceRecord record = retrieveDeviceRecord(handle);
        pauseDevice(handle);
        clearDeviceWorkQueue(handle);
        closeDevice(handle);
    }

    private DeviceHandle getHandle(DeviceID id) {
        ...
        throw new DeviceShutDownError("Invalid handle for: " + id.toString());
        ...
    }
    ...
}
```

### 비즈니스 예외를 위한 최상위 BusinessException 클래스
![image](https://user-images.githubusercontent.com/61215550/170408556-1b97ba89-a3d5-4ee6-b336-9993824a3c9a.png)
- 최상위 BusinessException 기준으로 예외를 발생시키면 통일감 있는 예외 처리 가질 수 있음. 

### 컨트롤러 예외 처리 ✔ >> 컨트롤러의 중요한 책임 `검증` 
- 컨트롤러에서 모든 요청에 대한 값 검증을 진행 >> 이상이 없을 시에 서비스 레이어 호출
- ⭐ 컨트롤러의 책임을 다하지 않으면 그 책임은 자연스럽게 다른 레이어로 전해짐 >> 결국 큰 비용과 유지보수 하기 어려워짐 ㅠ,ㅠ
- 모든 예외 `@ControllerAdvice` 선언된 객체에서 핸들링
  - 컨트롤러로 본인이 직접 예외처리 않고 예외가 발생하면 그냥 던져버리는 패턴으로 일관성 있게 개발 가능!

```java
@RestController
@RequestMapping("/members")
public class MemberApi {

    private final MemberSignUpService memberSignUpService;

    @PostMapping
    public MemberResponse create(@RequestBody @Valid final SignUpRequest dto) {
        final Member member = memberSignUpService.doSignUp(dto);
        return new MemberResponse(member);
    }
}
```


```java
public class SignUpRequest {
    @Valid private Email email;
    @Valid private Name name;
}

public class Name {
    @NotEmpty private String first;
    private String middle;
    @NotEmpty private String last;
}

public class Email {
    @javax.validation.constraints.Email
    private String value;
}
```

### Try Catch 전략 
- 기본적으로 예외 발생 시 >> 로직의 흐름을 끊고 종료 시켜야됨
  - 최대한 예외를 발생시켜 종료하는 것을 지향한다고 생각(주관적)
```java
try {
    // 비즈니스 로직 수행...
}catch (Exception e){
    e.printStackTrace();
}
```
- ✔ 이미 예외가 발생했음에도 다음 로직 실행된다!!! 이런 식의 `try-catch` 최대한 지양!!!!!!!!!!!!!!!!!!!!

```java
try {
    // 비즈니스 로직 수행...
}catch (Exception e){
    e.printStackTrace();
    throw new XXX비즈니스로직예외(e);
}
```
1. `try-catch` 최대한 지양
2. `try-catch` 에러를 먹고 주는 코드 지양(위 코드 있으면 로그라도 찍어주자...)
3. `try-catch` 사용하게 되면 더 구체적인 Exception 발생시키는 것이 좋음.
