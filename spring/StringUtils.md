## `StringUtils`
> [참고 자료](https://bigstupid.tistory.com/40)
> [참고 자료](https://hahaha2016.tistory.com/4)
- 문자열에 작업하는 관련기능들을 모아놓은 라이브러리
- 라이브러리 `commons-lang3` ✔

### 문자열 처리 클래스
#### 1. `StringUtils.isEmpty(CharSequence cs)`
- 값이 `null`인지 공백문자`("")` 이면 __true__ 값 반환

```java 
StringUtils.isEmpty(null) // true
StringUtils.isEmpty("") // true
StringUtils.isEmpty("str") // false
```

#### 2. `StringUtils.isNotEmpty(CharSequence cs)`
- 위와 반대로 동작

#### 3. `StringUtils.isAnyEmpty(CharSequence... css)`
- 문자들중 null이나 공백문자("") 있을 시 __true__ 반환

```java
StringUtils.isAnyEmpty(null) // true
StringUtils.isAnyEmpty(null, "str") // true
```

#### 4. `StringUtils.isNoneEmpty(CharSequene... css)`
- 3번과 반대로 동작

#### 5. `StringUtils.isAllEmpty(CharSequence... css)`
- 모든 문자열들은 null이거나 공백문자("")이면 __true__ 반환




