## WebAppContextSetup
> [참고자료](https://velog.io/@hanblueblue/Spring-mvc-standaloneSetup-vs-webAppContextSetup)
- `MockMvc`: 실제 네트워크 연결하지 않고 api 테스트 가능하도록 모킹된 객체
  - 웹 애플리케이션 >> 애플리케이션 서버 배포 x >> 스프링 mvc 동작 재현하는 클래스

### webAppContextSetup - [참고자료](https://incheol-jung.gitbook.io/docs/study/undefined-1/undefined-4)
- 실제 Spring MVC 구성을 로드 >> 완벽한 통합 테스트 수행
- 구성된 컨트롤러 한 개 이상을 포함하는 스프링 애플리케이션 컨텍스트 사용 >> Mock Mvc 생성

### standaloneSetup 
- 단위 테스트
- 수동으로 생성하고 구성한 **컨트롤러 한 개 이상**을 서비스할 Mock Mvc 생성

### (추가) MockMvc 모드 - [참고자료](https://itmore.tistory.com/entry/MockMvc-%EC%83%81%EC%84%B8%EC%84%A4%EB%AA%85)
- 사용자 정의 DI 컨테이너 모드
- 단독모드
#### ✔ 사용자 정의 DI 컨테이너 모드
```JAVA
@RunWith(SpringJUnit4ClassRunner.class)
@ContextHierarchy({
        @ContextConfiguration(classes = AppConfig.class),
        @ContextConfiguration(classes = WebMvcConfig.class)
})
@WebAppConfiguration
public class WelcomeControllerTest {

    @Autowired
    WebApplicationContext context;

    MockMvc mockMvc;

    @Test
    public void setUpMockMvc() {
        this.mockMvc = MockMvcBuilders.webAppContextSetup(context).build();
    }
    // ..
}
```
#### ✔ 단독 모드
- 스프링 MVC 설정 >> 스프링 테스트 측에서 설정
- 스프링 테스트가 생성된 DI컨테이너 사용 >> 스프링 MVC 재현
- 스프링 테스트의 각종 설정 >> 테스트 케이스 측에서 커스텀 가능
- 스프링 MVC 이용하면서도 단위 테스트 관점에서 컨트롤러 테스트


```JAVA
@Before
public void setUpMockMvc() {
    MockitoAnnotations.initMocks(this);
    this.mockMvc = MockMvcBuilders
            .standaloneSetup(controller)
            .addFilter(new CharacterEncodingFilter("UTF-8"))
            .build();
}
```

