## @Builder.Default @ColumnDefault 차이
> [참고자료](https://velog.io/@minji/%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8-JPA-%EC%97%94%ED%8B%B0%ED%8B%B0-%EC%BB%AC%EB%9F%BC-default-value-%EC%84%A4%EC%A0%95%ED%95%98%EA%B8%B0-ColumnDefault-Builder.Default-%EC%B0%A8%EC%9D%B4)
- `@ColumnDefault`: DDL에 포함할 칼럼의 기본값 지정
- `@Builder.Default`: 객체 생성시 기본값



```java
@ColumnDefualt("DDL 기본값")
@Builder.Default()
private int value = 0;
```
