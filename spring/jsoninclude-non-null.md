## Spring JSON 응답값 NULL인 필드 제외
> [참고자료](https://bestinu.tistory.com/45)

```JAVA
@Getter
@JsonInclude(JsonInclude.Include.NON_NULL) // Null 값인 필드 제외
@Builder
public class UserResponseDto {
    private String email;
    private String nickname;
}
```
