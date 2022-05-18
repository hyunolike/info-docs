## `SpringMVC` >> `Ajax` `JSON` 서버에서의 Data 셋팅방법 ✔
> [참고 자료](https://www.nextree.co.kr/p11205)
- Ajax 통신의 전송형식 >> `CSV` `XML` `Json` ... 등등

### 1. `response` 객체에 문자열 담기
- `HttpServletResponse` 객체에 __문자열__ 담아 보내는 방법
- Servlet 기반이니까 SpringMVC 뿐만 아니라 Servlet 기반의 타 프레임워크도 사용 가능

### 2. `ObjectMapper`
- 이걸 사용해도 `HttpServletResponse` 객체 사용
- `jackson-databind` 라이브러리 추가(필수)

### 3. `@ResponseBody`
### 4. `JsonView`

## 리턴 타입 정리
> [참고 자료](https://ooeunz.tistory.com/101)
### 1. `String`
- Spring + View template
```java
@GetMapping("/test")
public String test(Model model){
  model.addAttribute("data", data);
  return "/test/data";
}
```
#### 1-1. 종류
- `Model & ModelMap`
  - Model >> 인터페이스
  - ModelMap >> 구현체
  - 스프링 내부적으로 개체의 타입이 동일✔
- `ModelAndView`
  - Model + View 동시 설정 가능한 객체
- `redirect`
  - 지정한 페이지 리다이렉트
- `void`

### 2. `Map`
- 키, 값

### 3. `@RestController`
- Restful Controller 준말
- `@Controller` + `@ResponseBody`
