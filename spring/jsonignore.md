## `@JsonIgnore` `@JsonIgnoreProperties` `@JsonIgnoreType` - json 직렬화, 역직렬화 속성 무시하는데 사용
> [참고자료](https://velog.io/@hth9876/JsonIgnorePropertiesignoreUnknown-true)

- `Jackson`: 서버와 클라이언트간에 데이터 전송을 json 타입으로 전송할 수 있게 해줌!!✅
- 직렬화: 객체의 직렬화는 객체의 내용을 바이트 단위로 변환 / 파일 또는 네트워크를 통해서 스트림(송수신) 가능하도록 하는 것 의미


|어노테이션|설명|
|---------|---------|
|`@JsonIgnore`| 클래스의 속성(필드, 멤버변수) 수준에서 사용|
|`@JsonIgnoreProperties`| 클래스 수준(클래스 선언 바로 위에) 사용|
|`@JsonIgnoreType`| 클래스 수준에서 사용 / 전체 클래스 무시|


### 1. @JsonIgnore
- 직렬화 역직렬화 사용되는 논리적 속성.. 값 무시할 때 사용
- `@JsonIgnore(false)`: 비활성화 / json 역직렬화, 직렬화 가능해짐


```java
@jsonIgnore
public String myName; ✅직렬화 할 때 json 필드에 담지 않지만 역직렬화할 때 에러 발생 ㅠ,ㅠ Unrecognized field "myName"

위와 같은 문제를 아래 코드 추가로 해결!! ✅ 직렬화는 물론 역직렬화 시 필드 무시 가능해짐 :)
@JsonIgnore 
@JsonProperty("Name")
private String myName;


또한 게터 세터 메서드에서도 사용 가능하다.

@JsonIgnore
public String getmyName(){
	return this.myName;
}

@JsonIgnore
public void setmyName(String myName){
	return this.myName = myName;
}
```

### 2. @JsonIgnoreProperties
- 클래스 단위


```java
@JsonIgnoreProperties({ "bookName", "bookCategory" })
public class Book {public class Book {
	@JsonProperty("bookId")
	private String id;private String id;
    
	@JsonProperty("bookCategory")
	private String category;
  
  
--- 😛옵션
✅ 특정 필드 직렬화 허용 / 역직렬화 허용 안함!
@JsonIgnoreProperties
(
value={"bookName","bookCategory"}, allowGetters=true
)

✅ 특정 필드 역직렬화 허용 / 직렬화 허용 안함!
@JsonIgnoreProperties
(
value={"bookName","bookCategory"}, allowSettersa=true
)

✅ 역직렬화, json 프로퍼티 중에 자바 class의 vo 프로퍼티 없는 경우 에러 던지지 않고 무시! (아래 참고)
@JsonIgnoreProperties(ignoreUnknown = true)
```


```java
##Class Person ###

import com.fasterxml.jackson.annotation.JsonIgnoreProperties;
@Data	//lombok
@JsonIgnoreProperties(ignoreUnknown = true)
public class person{
	private String name;
    	private int age;
}


##JSON##

{
	"name" : "han",
    	"age"  : "29",
        "language" : "korean",
        "gender" : "male"
}
```

### 3. @JsonIgnoreType
- 클래스 레벨
- 클래스 내에 존재하는 모든 필드 직렬화, 역직렬화 무시
