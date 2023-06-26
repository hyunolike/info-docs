## Spring Security 비밀번호 검사는? `DaoAuthenticationProvider`
> [참고자료](https://github.com/HomoEfficio/dev-tips/blob/master/Spring%20Security%EC%9D%98%20%EC%82%AC%EC%9A%A9%EC%9E%90%20%EB%B9%84%EB%B0%80%EB%B2%88%ED%98%B8%20%EA%B2%80%EC%82%AC.md)
- `UserDetailService` 인터페이스 / `loadUserByUsername(String username)` >> 사용자 정보 db 조회 및 반환
-  비밀번호 체크는 어디서??


```java
    String presentedPassword = authentication.getCredentials().toString();

		if (!passwordEncoder.matches(presentedPassword, userDetails.getPassword())) {
			logger.debug("Authentication failed: password does not match stored value");

			throw new BadCredentialsException(messages.getMessage(
					"AbstractUserDetailsAuthenticationProvider.badCredentials",
					"Bad credentials"));
		}
```
