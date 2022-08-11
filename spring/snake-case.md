## Requeest-Body를 `snake case` 값을 `camel case` 로 파싱 방법

### 1. @JsonNaming
```java
@JsonNaming(PropertyNamingStrategy.SnakeCaseStrategy.class)
public class UserDTO{
  private String firstName;
  private String lastName;
}
```

### 2. application.yml
```yml
spring.jackson.property-naming-strategy=SNAKE_CASE
```
