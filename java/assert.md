## `assert` 키워드
> [참고 자료](https://www.delftstack.com/ko/howto/java/java-assert/) <br>
> [실행 옵션 설정관련 자료](https://velog.io/@jamie/assert)

- 프로그램에 대한 가정을 하는 테스트하는데 사용
- 개발/테스트 단계에서 파라미터가 제대로 넘어왔는지 계산이 제대로 됬는지 혹은 특정 메소드가 작동하는 한계상황(Null이 들어오면 작동x) 을 정하는 용도로 사용!

### 0. 선작업 - 실행옵션 세팅
- 해당 실행 설정에서 `-ea` 추가 ✔
- ![image](https://user-images.githubusercontent.com/61215550/165669353-963ac8cb-761d-4667-b16b-96911efb5117.png)

#### 0.1 유효성 검사 사용
- 옵션
  - 유효성 검사 포함: `-enableassertions` `-ea`
  - 유효성 검사 배제: `-disableassertions` `-da`

- 옵션 값 설정
  - 옵션만 명시하는 경우: 전체 적용
  - 클래스명 명시하는 경우: 해당 클래스에 적용
  - 패키지명... 명시하는 경우: 해당 패키지와 하위 패키지의 모든 클래스에 적용
  - `ea`와 `da`는 같이 쓸 수 있음
  - 설정 예


```java
-ea Main : 시스템 클래스를 제외한 모든 클래스 활성화
-ea:<class name> Main : 지정한 <클래스>만 활성화
-ea:... Main : 기본 패키지를 활성화 = 전체 패키지 활성화(모든 클래스와 하위 패키지 포함)
-ea:<package name>... Main : 지정된 <패키지> 활성화(모든 클래스와 하위 패키지 포함)
-ea -da:<class name> Main : 지정된 클래스를 제외한 모두 활성화
-ea -da:<package name>... Main : 지정된 패키지를 제외한 모두 활성화
```

### 1. `조건` 으로 사용
- 프로그램에서 버그를 감지하고 수정하는 가장 빠르고 쉬운 방법
- assert는 실행될 때 참으로 간주 그렇지 않으면 거짓이며 오류 발생

```java
String[] names = {"john", "Mary", "Davic"};
assert names.length == 2: "에러 발생 ㅠ,ㅠ";
System.out.println("Threr is " + names.length + " names in an array");
```

![image](https://user-images.githubusercontent.com/61215550/165669466-a62e3796-dd3a-42c3-994d-2c6d7fc4e3a1.png)

### 2. 선언법
```java
assert 조건식
assert 조건식: AssertionError메세지

assert false;
Exception in thread "main" java.lang.AssertionError
	at test.Main.main(Main.java:23)
    
assert false: "단언문 실패 메세지입니다.";
// 발생 Exception
Exception in thread "main" java.lang.AssertionError: 단언문 실패 메세지입니다.
	at test.Main.main(Main.java:23)
```

