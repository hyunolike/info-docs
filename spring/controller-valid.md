## Controller 값 검증 `@Valid` (데이터 유효성 검증) - `업데이트 22/03/30`
> [참고자료](https://mangkyu.tistory.com/174)
### `@Valid`
- 빈 검증기 이용 >> 객체의 제약 조건을 검증하도록 지시하는 어노테이션
- 모든 요청 `프론트 컨트롤러(디스패처 서블릿)` 통해 컨트롤러 전달 ⭐
  - `ArgumentResolver`에 의해 처리
  - `@Valid` 기본적으로 컨트롤로에만 동작 >> 다른 계층에서는 검증 진행 x >> 💡 다른 계층 검증하기 위해서는 `@Validated` 와 결합 진행!

### `@Validtaed` - 🍃Spring framework 제공
- ⭐ 입력 파라미터 >> 최대한 컨트롤러에서만 최대한 처리!
- `Spring AOP` 기반으로 메소드의 요청을 가로채서 유효성 검증 진행해줌


```java
@Service
@Validated
public class UserService {

	public void addUser(@Valid AddUserRequest addUserRequest) {
		...
	}
}
```

---
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
