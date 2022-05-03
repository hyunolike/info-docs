## Spring Profiles
> [참고 자료](https://velog.io/@gillog/Spring-profile%EB%A1%9C-%EC%84%9C%EB%B2%84-%ED%99%98%EA%B2%BD%EC%97%90-%EB%A7%9E%EB%8A%94-Context-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0-Dspring.profiles.active)
- 애플리케이션 실행되는 환경에 따라 다른 Bean 매핑
- 예시) 개발 환경, 스테이징 환경, 실 서비스 환경에 따라 __다른 의존성 주입 가능__⭐
- `profile` 3가지 방법으로 활성화 할 수 있는 논리적 그룹
  1. `ConfigurableEnvironment.setActiveProfiles(java.lang.String ...)` (Application Code)
  2. `spring.profiles.active` Property 지정(JVM 시스템 속성, 환경 변수)
  3. `web.xml` (tomcat) 



