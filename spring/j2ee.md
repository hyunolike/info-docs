## `J2EE` - Java 2 Enterprise Edition
> [참고자료](https://gyrfalcon.tistory.com/entry/J2EE)
- 자바 기술로 기업환경의 어플리케이션을 만드는데 필요한 스펙들을 모아둔 스펙 집합
### 기본 특징
- 언어는 Java, 플랫폼은 자유 ⭐
  - JVM 이라는 가상 머신을 통해 각 OS에 맞게 바이트 코드로 변환되어 실행!
### 구성 요소
- `Sevlet`: 클라이언트가 보내느 HTTP 요청을 처리하는 서버측 자바 프로그램, Servlet 엔진 있어야 됨
- `JSP(Java Server Pages)`: HTML이나 Java 코드 써서 사용자에게 정보 보여줌 / JSP 처음 실행될 때 Servlet 엔진이 이것을 Servlet으로 컴파일시켜서 내부적으로 Servlet으로 동작
- `EJB(Enterprise Java Beans)`: Java에서 제공하는 분산 컴포넌트 기술로 비즈니스 로직이나 데이터, 메시지 처리 가능
- `Remote Method Invocation(RMI)`: 프록시 써서 원격에 있는 Java 객체의 메소드를 실행시키기 위한 기술
- `Java Naming DirectoryInterface(JNDI)`: 자바 기술로 만들어진 객체에 이름을 붙여 찾을 수 있도록 단일한 인터페이스 제공
- `Java Database Connector(JDBC)`: 여러 종류의 데이터베이스 시스템에 접근하는 단일한 인터페이스 제공
- `Java Connector Architecture(JCA)`: 이기종 플랫폼을 통합할 수 있도록 플랫폼 독립적인 인터페이스 제공
- `Java Message Service(JMS)`: 여러 가지 메시징 시스템에 대한 플랫폼 독립적인 인터페이스 제공

### [참고자료](https://harrydony.tistory.com/52)
