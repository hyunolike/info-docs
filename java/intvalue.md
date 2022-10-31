## `intValue()` `parseInt()`
> [참고자료](https://java119.tistory.com/30)

### parseInt()
- string형 객체에서 int형 값을 뽑아내는 메소드
- 내용물(String) -> 내용물(int)


```java
String s = "1";
int i = Integer.parseInt(s); // 1
```

### intValue()
- Integer 객체에서 int형 값을 뽑아내는 메소드
- Integer -> (언박싱) -> int 변환

