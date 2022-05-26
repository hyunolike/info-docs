## Controller 값 검증 `@Valid` (데이터 유효성 검증) 
- `@Valid` 이용시 서비스단이 아닌 객체 안에서 들어오는 값을 검증 가능해짐
- 기존 spring boot 버전업이 되면서 web 의존성 안에 있는 constraints package가 모듈로 빠져나옴
  - `implementation 'org.springframework.boot:spring-boot-starter-validation'` ✔

### `@Valid`
- @RequestBody 통해 데이터 바인딩 하는 경우
```java
import javax.validation.constraints.NotEmpty;

public class User {
    private Integer id;
    @NotEmpty
    private String account;
    @NotEmpty
    private String password;

    // 생략
}
```
- 컨트롤러 메소드 파라미터로 `BindingResult` 타입 변수 추가
```java
@RequestMapping(value = "/valid", method = RequestMethod.POST)
public ResponseEntity login(@RequestBody @Valid User user, BindingResult bindingResult) {
    if (bindingResult.hasErrors()) {
        List<ObjectError> errorList = bindingResult.getAllErrors();
        for (ObjectError error : errorList)
            System.out.println(error.getDefaultMessage());
    }
    ...
}
```
- 위 코드 이해하기
  - @Valid 선언으로 User클래스의 제약조건에 따라 데이터 유효성 검사 진행
  - 모든 속성의 데이터가 유효하면 아무일 안일어남
  - 데이터가 유효하지 않는 속성이 있으면 그에 대한 에러 정보를 BindingResult 변수에 담아준다!! ✔

### `@Validated` >> 유효성 검사 모두 말고 원하는 것만 할 수 있게 해주는 것!! 
- 기본적인 기능인 `@Valid`와 기능 동일 >> 속성 제약조건에 대한 그룹을 만들어 적용 가능 ✔
- 원하는 속성만 유효성 검사를 하고 싶은 경우에 사용하는 것!! 기존 @Valid는 달아놓은 속성에 대해 전부 유효성 검사 진행!
- `ValidationGroup.java`
```java
public class ValidationGroups {
    public interface group1 {};
    public interface group2 {};
}
```
- `User.java`
```java
public class User {
    private Integer id;
    @NotEmpty(groups = {ValidationGroups.group1.class})
    private String account;
    @NotEmpty(groups = {ValidationGroups.group2.class})
    private String password;
}
```
- `Controller`
```java
@RequestMapping(value = "/user/login", method = RequestMethod.POST)
public ResponseEntity login(@RequestBody @Validated(ValidationGroups.group1.class) User user, BindingResult bindingResult) {
    // do something
}
```
