## Spring AOP - `ProceedingJoinPoint`
> [참고자료](https://velog.io/@dhk22/Spring-AOP-%EA%B0%84%EB%8B%A8%ED%95%9C-AOP-%EC%A0%81%EC%9A%A9-%EC%98%88%EC%A0%9C-Logging)

### 1. AOP
- (부가적인) 공통의 기능 분리
- 한 개 모듈(메서드)는 자신의 비즈니스 로직에만 집중


```gradle
implementation 'org.springframework.boot:spring-boot-starter-aop'
```


```java
@Slf4j
@Aspect
@Component
public class SimpleLogAop {

    // com.aop.controller 이하 패키지의 모든 클래스 이하 모든 메서드에 적용
    @Pointcut("execution(* com.aop.controller..*.*(..))")
    private void cut(){}

    // Pointcut에 의해 필터링된 경로로 들어오는 경우 메서드 호출 전에 적용
    @Before("cut()")
    public void beforeParameterLog(JoinPoint joinPoint) {
        // 메서드 정보 받아오기
        Method method = getMethod(joinPoint);
        log.info("======= method name = {} =======", method.getName());

        // 파라미터 받아오기
        Object[] args = joinPoint.getArgs();
        if (args.length <= 0) log.info("no parameter");
        for (Object arg : args) {
            log.info("parameter type = {}", arg.getClass().getSimpleName());
            log.info("parameter value = {}", arg);
        }
    }

    // Poincut에 의해 필터링된 경로로 들어오는 경우 메서드 리턴 후에 적용
    @AfterReturning(value = "cut()", returning = "returnObj")
    public void afterReturnLog(JoinPoint joinPoint, Object returnObj) {
        // 메서드 정보 받아오기
        Method method = getMethod(joinPoint);
        log.info("======= method name = {} =======", method.getName());

        log.info("return type = {}", returnObj.getClass().getSimpleName());
        log.info("return value = {}", returnObj);
    }

    // JoinPoint로 메서드 정보 가져오기
    private Method getMethod(JoinPoint joinPoint) {
        MethodSignature signature = (MethodSignature) joinPoint.getSignature();
        return signature.getMethod();
    }
}
```


|용어|설명|
|----|-----------|
|`@Aspect`|AOP 설정 클래스|
|`Pointcut`|특정 조건으로 JoinPoint 필터링(패키지 단위, 클래스 단위, 메서드 단위, 어노테이션 단위 ...) ✔ `Aspect` 적용할 위치|
|`JoinPoint`|Aspect 적용시킬 수 있는 모든 지점 <br> Pointcut은 `Joinpoint` 특정 조건으로 걸러낸 것(부분집합 정도)<br>`JoinPoint`를 매개변수 받는 경우 런타임 메서드 정보 알아낼수 있음|
|`@Before`|호출전| 
|`@AfterReturning`|예외 없이 정상적으로 리턴 후!|
