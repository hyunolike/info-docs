## @NoargsConstructor(AccessLevel.PROTECTED) 와 @Builder
> [참고자료](https://cobbybb.tistory.com/14)
- `@NoargsConstructor(AccessLevel.PROTECTED)`

### 1. 사용 이유
- 무분별한 객체 생성에 대해 한번 더 체크할 수 있는 수단!! 이용

#### 2. @NoargsConstructor(AccessLevel.PROTECTED) + @Builder
- 의미 있는 객체 생성하기 위한 좋은 방법이자 제약조건

```java
@NoArgsConstructor(access = AccessLevel.PROTECTED)
public class User {
    private String name;
    private Long age;
    private String email;

    @Builder
    public User(Long age, String email) {
        this.name = "test_name";
        this.age = age;
        this.email = email;
    }

    @Builder
    public User(String name, Long age, String email) {
        this.name = name;
        this.age = age;
        this.email = email;
    }
}
```
