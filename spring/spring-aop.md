## AOP (Aspect-Oriented Programming)
> [참고자료](https://backtony.github.io/spring/2021-09-12-spring-aop-0/) <br> 
> 🕹 공통된 기능을 재사용하는 기법
- ✔ 애플리케이션 전체에 걸쳐 사용되는 기능을 재사용하도록 지원하는 것
  - 관점(관심) 지향 프로그래밍
  - ![image](https://user-images.githubusercontent.com/61215550/223917292-0e0e8e8c-7812-4148-b483-8710bfe2d803.png)
- ✌ 장점
  - 흩어진 공통 기능 >> 하나의 장소
  - 다른 서비스 모듈들이 본인의 목적에만 충실 + 그외 사항들은 신경쓰지 않는다는 점

|OOP|AOP|
|---|---|
|비즈니스 로직의 모듈화|인프라 혹은 부가기능의 모듈화|
|모듈화의 핵심 단위는 **비즈니스 로직**|각각의 모듈들의 주 목적 외에 필요한 부가적인 기능들|

### 1. 주요 개념
#### 1-1. Target 
- 부가기능을 부여할 대상(클래스) `Aspect`
#### 1-2. Aspect 
- 핵심 기능에 부가되어 의미를 갖는 특별한 모듈 `
- 부가기능 어디에 적용할지 `PointCut`
- ✌ 애플리케이션 핵심적인 기능에서 부가적인 기능을 분리 Aspect 모듈을 만들어 설계하고 개발하는 방법 >> AOP
#### 1-3. Advice
- `Aspect` 실질적으로 어떤 일 해야할지 부가기능을 담은 구현체
- Aspect `무엇`을 `언제`할지를 정의
#### 1-4. JoinPoint
- `Advice` 적용될 위치
#### 1-5. PointCut
- 부가기능이 적용될 대상(메서드) 선정하는 방법 
#### 1-6. Proxy
- Target 감싸서 Target에 들어오는 `요청을 대신 받아주는 Warpping 오브젝트` ✔
#### 1-7. Introduction
- Target 클래스 >> 코드 변경 없이 >> 신규 메서드 / 멤버변수 추가하는 기능
#### 1-8. Weaving
- 지정된 객체에 `Aspect` 적용 >> 새로운 Proxy 객체 생성하는 과정 의미

### 2. 동작 과정
> [참고자료]
- ![image](https://user-images.githubusercontent.com/61215550/223918494-c76a0f92-4519-43fa-88b4-cb2aa49b2801.png)

### 3. 애노테이션 동작 순서
- ![image](https://user-images.githubusercontent.com/61215550/223918570-5c2177c0-231b-43a9-9496-2240606251bc.png)
#### 3-1. `@Order` 클래스에만 적용 가능
```java
@Slf4j
public class AspectV5Order {

    @Aspect
    @Order(1)
    public static class TxAspect {
        @Around("hello.aop.order.aop.Pointcuts.orderAndService()")
        public Object doTx(ProceedingJoinPoint joinPoint) throws Throwable {
            // 생략
        }
    }

    @Aspect
    @Order(2)
    public static class LogAspect {
        @Around("hello.aop.order.aop.Pointcuts.allOrder()")
        public Object doLog(ProceedingJoinPoint joinPoint) throws Throwable {
            // 생략
        }
    }    
}
```
