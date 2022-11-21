## Dispatcher Servlet
> [참고자료](https://incheol-jung.gitbook.io/docs/q-and-a/spring/spring-web-mvc)
- 외부의 요청을 특정 컨트롤러로 매핑하기 위해 `Front Controller` 패턴 적용한 Servlet!
  - 이전 >> 서블릿을 컨트롤러 당 하나씩 두고 있어서 컨트롤러가 추가될 때마다 서블릿 설정도 추가해야 되는 불편 ㅠ,ㅠ
  - ✔ `dispatcher servlet` >> 컨트롤러 추가시 별도의 servlet 설정 필요가 없어짐!
  - ✔ `dispatcher servlet` >> `Tracking` or `Security` 적용 시 편하게 구현 가능 및 url 구성 간편! 오옹

### 동작 순서
- ⭐ 클라이언트 해당 어플리케이션 접근하면 가로채기이~
- 어떻게 가로채?
  - `web.xml` 등록된 dispatcherServlet의 `<url-pattern>` `/` 같이 해당 어플 통과하는 모든 url 등록했기에
  - 특정 url만 적용하고 싶으면 `<url-pattern>` 내용 변경해주자! - 😛 스프링부트에선 `application.yml` 에서 옵션 설정하면되!


```xml
<servlet>
  <servlet-name>salesServlet</servlet-name>
  <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
  <!-- contextLoader가 해당 위치의 설정 파일을 읽어, 해당 파일을 dispatcher servlet으로 만든다. -->
  <init-param>
    <param-name>contextConfigLocation</param-name>
    <param-value>/WEB-INF/salesServlet-servlet.xml</param-value>
  </init-param>
  <load-on-startup>1</load-on-startup>
</servlet>

<!-- /sales로 시작하는 url 요청을 받아 salesServlet에서 처리한다. -->
<servlet-mapping>
  <servlet-name>salesServlet</servlet-name>
  <url-pattern>/sales</url-pattern>
</servlet-mapping>
```
### ⭐ `Fiter` `Intercepter` `AOP` 수행 시점 >> **dispatcherServlet` 기준으로 볼래
- ![image](https://user-images.githubusercontent.com/61215550/202963370-42314e35-15eb-4c8b-8129-44f1dc23c3d5.png)
