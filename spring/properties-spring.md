## `properties` 속성값 가져와서 사용 방법
> [참고 자료](https://bcp0109.tistory.com/227)
- spring boot 프로젝트가 커지면 사용되는 __글로벌 값__ 별도 관리 필요!
- `@Value` 어노테이션: `properties` 파일에 세팅한 내용을 __Spring__ 변수에 주입하는 역할 

### `@Value("")` 사용
```java
@RestController
public class ValueController {

    @Value("Hello World")
    private String greetingMessage;

    @GetMapping("")
    public String sendGreeting(){
        return greetingMessage;
    }
}
```

### `@Value("${...}")` 사용
- ✔ 속성값은 __런타임__ 에 변수로 주입되며 만약 속성값이 properties 파일에 없다면 오류 발생ㅠ,ㅠ
  - 오류 방지를 위해 `@Value("${greeting.message: Greeting not found!}")` 처럼 콜론 붙이고 뒤에 기본값 설정하자 !!
`application.properties`
```java
greeting.message=Hello World!
```


```java
@RestController
public class ValueController {

    @Value("${greeting.message}") 
    private String greetingMessage;

    @GetMapping("")
    public String sendGreeting(){
        return greetingMessage;
    }
}
```

### `@Value("${...}")` 리스트 사용
`application.properties`
```java
my.weekdays=Mon,Tue,Wed,Thu,Fri
```


```java
@Value("${my.weekdays}")
private List<String> strList; // injects [Mon, Tue, Wed, Thu, Fri]

//Providing default value
@Value("${my.weekends:Sat,Sun,Fri}")
private List<String> strList2; // injects [Sat, Sun, Fri
```
