## `MockMvc` >> 통합테스트 관점 ✔
- 서블릿 컨테이너 ❌ >> 시뮬레이션된 mvc 환경에 모의 http 서블릿 요청을 전송하는 기능을 제공하는 유틸리티 클래스
- 웹 애플리케이션을 애플리케이션 서버에 배포하지 않고도 스프링 mvc의 동작 재현

### MockMvc 주입받는 2가지 ✔
> [참고 자료](https://siyoon210.tistory.com/145)
1. `@SpringBootTest` + `@AutoConfigureMockMvc` >> 통합 테스트 진행할 떄 사용
2. `@WebMvcTest` >> MVC 쪽만 슬라이스 테스트 진행 시 사용

### 예시
```java
@Test
public void helloModelTest() throws Exception {
 mockMvc.perform(MockMvcRequestBuilders.get("/hello").accept(MediaType.TEXT_HTML))
         .andExpect(MockMvcResultMatchers.status().isOk())
         .andExpect(MockMvcResultMatchers.model().attribute("name", "siyoon"))
         .andDo(MockMvcResultHandlers.print());
}
```

- 아래와 같이 짧게 코드 작성 가능하지만 ✔ 
- 어떤 메소드가 있는지 알기 어려워 테스트코드 작성에 익숙하지 않다면 명시하는 것 추천
```java
@Test
public void helloTest() throws Exception {
      mockMvc.perform(get("/hello").accept(MediaType.TEXT_HTML))
              .andExpect(status().isOk())
              .andDo(print());
}
```
