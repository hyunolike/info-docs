## 원인 예외 `chained exception`
> [참고자료](https://devbksheen.tistory.com/entry/%EC%97%B0%EA%B2%B0%EB%90%9C-%EC%98%88%EC%99%B8chained-exception)
- 원인 예외 등록 + 다시 예외 발생
- 여러가지 예외를 하나의 큰 예외로 묶어서 사용 하기 위해 ✔

### 왜 연결?
1. 큰 분류의 예외로 묶어서 다루기 위함
2. 상속 관계 무시 가능
3. checked 예외 >> unchecked 예외로 바꿀 수 있음!

### 예제 코드
```java
@Getter
public class GlobalException extends RuntimeException {

    private final String errorCode;
    private final String message;

    public GlobalException(ErrorType errorType) {
        this.errorCode = errorType.getErrorCode();
        this.message = MessageUtil.getMessage(errorType);
    }

    public GlobalException(ErrorType errorType, Throwable throwable) {
        this(errorType);
        this.initCause(throwable);
    }
}
```
