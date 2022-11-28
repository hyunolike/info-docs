## JSP 데이터 전달 방법
> [참고자료](https://jddng.tistory.com/103)
- ✔ `ViewResolver`
  - 컨트롤러에서 전달받은 View 이름 토대로 JSP 찾아주기 >> JSP에서 사용하는 데이터 분석 후 응답 결과 만들어 전달하는 요소
### 📌 전달 방법 4가지
1. `param`
2. `HttpServletRequest`
3. `Model`
4. `ModelAndView`

#### 1. param
```html
<a href='test1?data1=100&data2=200'>test1</a><br/>
```


```java
@Controller
public class testController {

	@GetMapping("/test1")
	public String test1() {
		return "test1";
	}
}
```


```html
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>

<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
	<h1>test1</h1>
	<h3>data1 : ${param.data1 }</h3>
	<h3>data2 : ${param.data2 }</h3>
</body>
</html>
```
#### 2. HttpServletRequest 객체 사용
```java
@Controller
public class testController {

	@GetMapping("/test2")
	public String test2(HttpServletRequest request) {
		
		request.setAttribute("data1", 100);
		request.setAttribute("data2", 200);
		
		return "test2";
	}
}
```
#### 3. Model - Model 객체 = HttpServletRequest 객체 저장
```java
@Controller
public class testController {

	@GetMapping("/test3")
	public String test3(Model model) {
		
		model.addAttribute("data1", 300);
		model.addAttribute("data2", 400);
		
		return "test3";
	}
}
```
#### 4. ModelAndView - ✔ Model값 저장하는 기능 + View 이름 지정하는 기능
```java
@Controller
public class testController {

	@GetMapping("/test4")
	public ModelAndView test4(ModelAndView mv) {
		mv.addObject("data1", 100);
		mv.addObject("data2", 200);
		
		mv.setViewName("test4");
		return mv;
	}
}
```
