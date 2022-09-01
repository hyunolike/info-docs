## 프록시 & 내부 호출
> [참고자료](https://velog.io/@hyun6ik/%ED%94%84%EB%A1%9D%EC%8B%9C%EC%99%80-%EB%82%B4%EB%B6%80-%ED%98%B8%EC%B6%9C)

### 1. 내부 호출 문제점
- 자바 언어 >> 메소드 앞에 별도의 참조 없으면 `this` 라는 뜻으로 자기 자신의 인스턴스 가리킴...
- 프록시 방식의 AOP 한계
  - 스프링은 프록시 방식의 AOP 사용
  - 프록시 방식의 AOP는 메소드 내부 호출에 프록시 적용 불가 X
- `AspectJ` 사용하면 문제 발생하지 않음 !!! ✔
  - 해당 코드는 AOP 적용 코드가 붙어있기에 내부 호출과 무관하게 AOP 사용 가능
  - 하지만 로드 타임 워빙 사용 >> 설정 복잡 / JVM 옵션 줘야 ㅠ,ㅠ

### 2. 대안
#### 2.1 자기 자신 주입 - `Spring 2.6` 부터 ❌
```java
@Slf4j
@Component
public class CallServiceV1 {

    private CallServiceV1 callServiceV1;

    @Autowired
    public void setCallServiceV1(CallServiceV1 callServiceV1) {
        this.callServiceV1 = callServiceV1;
    }

    public void external() {
        log.info("call external");
        callServiceV1.internal(); // 외부 메소드 호출
    }

    public void internal() {
        log.info("call internal");
    }
}
```
#### 2.2 지연 조회
- 위와 같은 대안 해결 위해 스프링 빈 지연시켜 조회!
- 여기에서 자기 자신을 주입받는 것이 아니기에 **순환 사이클** 발생 X
  - `ObjectProvider(Provider)` `ApplicationContext` 사용


```java
@Slf4j
@Component
@RequiredArgsConstructor
public class CallServiceV2 {

    private final ObjectProvider<CallServiceV2> callServiceProvider;

    public void external() {
        log.info("call external");
        final CallServiceV2 callServiceV2 = callServiceProvider.getObject();
        callServiceV2.internal(); // 외부 메소드 호출
    }

    public void internal() {
        log.info("call internal");
    }
}

@Slf4j
@Import(CallLogAspect.class)
@SpringBootTest
class CallServiceV2Test {

    @Autowired
    CallServiceV2 callServiceV2;

    @Test
    void external() {
        callServiceV2.external();
    }

}
```

#### 2.3 구조 변경 ⭐가장 이상적인 방법~~
```java
/**
 * 구조를 변경(분리)
 */
@Slf4j
@Component
@RequiredArgsConstructor
public class CallServiceV3 {

    private final InternalService internalService;

    public void external() {
        log.info("call external");
        internalService.internal();
    }
}

@Slf4j
@Component
public class InternalService {

    public void internal() {
        log.info("call internal");
    }
}
```

