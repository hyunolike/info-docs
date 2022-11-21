## `Transaction` `2022/11/21 추가`
### (추가) `@Transactional`
> [참고자료](https://incheol-jung.gitbook.io/docs/q-and-a/spring/transactional)
#### 1. commit & rollback 
- `CheckedException` 예외 없을 때 >> commit
- `UncheckedException` 발생하면 >> rollback 
#### 2. 우선순위
1. 클래스 메소드
2. 클래스
3. 인터페이스 메소드
4. 인터페이스

#### 3. 주의 ⭐
- `@Transactional` + `Spring AOP` 함께 사용! >> 기본적으로 Dynamic Proxy 이용
  - 인터페이스 기반 동작 >> 인터페이스 없을 경우 트랜잭션 동작 x
- 인터페이스 없이 동작할려면!
  - `CGLib(Code Generation Library)`
- `public method` 에서만 적용!
  - 프록시 기반이니까!
---
- 트랜잭션 ✔ 
  - 여러 작업을 진행하다가 문제가 생겼을 경우 이전 상태로 롤백하기 위해 사용
  - 더 이상 쪼갤 수 없는 최소 작업 단위
### 스프링 제공하는 트랜잭션 핵심 기술 
1. 트랜잭션 동기화
  - 트랜잭션을 시작하기 위한 ✔Connection 객체를 특별한 저장소에 보관해두고 필요할 때 꺼내쓸 수 있도록 하는 기술
  - `Hibernate`는 ✔Session 객체 사용하기에 이를 해결하기 위해 __추상화__ 한 기술 사용
3. 트랜잭션 추상화
  - ![image](https://user-images.githubusercontent.com/61215550/165687865-35e8be63-6584-4b7c-886f-3de36d3fa971.png)
  - 트랜잭션 기술의 공통점을 담은 트랜잭션 추상화 기술
  - `JDBC` `JPA` `Hibernate` 등 >> 종속적인 코드를 이용하지 않고도 일관되게 트랜잭션 처리
  - 하지만 비즈니스 코드와 결합되어 2개의 책임을 갖고 있다는 점 >> `AOP` 이용해 트랜잭션 부분을 핵심 비즈니스 로직과 분리
5. AOP를 이용한 트랜잭션 분리
  - 마치 트랜잭션 코드와 같은 부가 기능 코드가 존재하지 않는 것처럼 보이기 위해 
  - 해당 로직을 클래스 밖으로 빼내서 별도의 모듈로 만드는 AOP(관점 지향 프로그래밍) 을 고안 및 적용 >> ⭐`@Transactional`

### 스프링에서 제공하는 트랜잭션 세부 설정
> [참고 자료](https://mangkyu.tistory.com/169)
- 트랜잭션 전파
- 격리수준
- 제한시간
- 읽기전용 
