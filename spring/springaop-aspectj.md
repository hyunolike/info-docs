## Spring AOP & AspectJ
> [참고자료](https://jiwondev.tistory.com/152)

### 1. Spring Proxy
- 스프링 AOP >> 프록시 기반 설계
  - 일반 프록시와 다름
  - 리플렉션 & 바이트코드 조작 >> 실제 타겟의 기능을 대신 수행 >> 기능 확장 + 추가(OCP 원칙) **다이나믹 프록시 객체** 의미!
#### 1-1. 용어
- Proxy: 대리인 의미 / 클라이언트-서버 등이 관계에서 중간에 끼어 대리인 역할 객체
### 2. JDK Dynamic Proxy
- 자바 API 사용 >> 인터페이스 기반 Proxy 생성
- 조작하는 기능 제공하지 않음

### 3. CGlib proxy
- 바이트 코드 조작 >> 프록시 객체 생성해주는 코드 생성 라이브러리
- ![image](https://user-images.githubusercontent.com/61215550/223282365-48019554-bf56-45e1-b344-5d982b8d164e.png)

---
### AspectJ vs Spring AOP
1. 기능과 목표 다름
  - Spring AOP: 스프링 컨테이너가 관리하는 빈에만 사용
  - AspectJ: 자바코드에서 동작하는 모든 객체에 사용 가능 / 성능 뛰어나고 기능 매우 강력 / 내부 구조 복잡 ㅠ,ㅠ
2. Weaving 방법 다름
  - Weaving: 공통관심사항(Aspect)의 동작코드(Advice) 대상 객체(Target)에 연결시켜 관점지향 구현한 객체로 만드는 과정
  - AOP 구현하기 위한 바이트 코드 조작 방법
### 비교
![image](https://user-images.githubusercontent.com/61215550/223282740-c6faf719-1b53-4e2c-b35d-70b26ff1e360.png)
