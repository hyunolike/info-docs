## Apache Tomcat
> [참고자료](https://velog.io/@hyunjae-lee/tomcat1)

- ✔ Apache 재단에서 만든 `Java Servlet` 지원하기 위한 오픈소스 프로젝트
  - 자바로 구성한 웹애플리케이션 실행시켜주는 소프트웨어 😛
- 자바 이용한 웹 애플리케이션의 다양한 규격 준수 / jsp, html 파일들로 구성된 `.war` 파일 배포해주는 엔진

### 구조
> ⭐자바로 작성된 프로그램이기 때문에 `JVM` 위에서 동작!
- ![image](https://user-images.githubusercontent.com/61215550/206639446-773db511-5c1a-4449-b805-97dc254e9ba5.png)
- `Coyote (HTTP Component)`: Tomcat에 TCP 통한 프로토콜 지원
- `Catalina (Servlet Container)`: Java Servlet 호스팅하는 환경
- `Jasper (JSP Engine)`: 실제 JSP 페이지 요청 처리하는 Servlet
