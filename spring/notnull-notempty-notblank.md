## `@NotNull` `@NotEmpty` `@NotBlank`
> [참고자료](https://sanghye.tistory.com/36)

### 차이점
|`@NotNull`|`@NotEmpty`|`@NotBlank`|
|---------|-------------|------------|
|`null`은 허용 x/ `""` `" "` 허용하게 됨|`null` `""` 허용 x / `" "` 허용|`null` `""` `" "` 모두 허용 x|

### ✔ 결론
- **DTO** 에 대한 테스트를 Validator에 따라 `null` `""` `" "` 구분해 나눠서 추가
- ⭐`DTO` 추가 이유 >> 각각의 request에 따라 테스트 코드를 추가해줄 수 있기 때문에 요청을 모두 검증 가능 / 테스트 코드에 대한 커버리지 높아짐!
