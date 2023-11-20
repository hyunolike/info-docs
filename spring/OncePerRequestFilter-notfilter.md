## `OncePerRequestFilter` 특정 URL 제외시키기
> [참고자료](https://velog.io/@yevini118/SpringBoot-OncePerRequestFilter-%ED%8A%B9%EC%A0%95-url-%EC%A0%9C%EC%99%B8%EC%8B%9C%ED%82%A4%EA%B8%B0)
### `shouldNotFilter()`
```java
@Override
protected boolean shouldNotFilter(HttpServletRequest request) throws ServletException {

    String[] excludePath = {"/user/signup", "/user/login", "/user/reissue"};
    String path = request.getRequestURI();
    return Arrays.stream(excludePath).anyMatch(path::startsWith);
}
```
