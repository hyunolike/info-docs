## Filter
> [참고자료](https://veneas.tistory.com/entry/Spring-Boot-%EC%8A%A4%ED%94%84%EB%A7%81-%EB%B6%80%ED%8A%B8-%ED%95%84%ED%84%B0-%EC%A0%81%EC%9A%A9-Filter)
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/3cab0f4f-f19e-4cf3-9c7b-64c40d9e5be6)
- ⭐ 공통 처리
  - 인터셉터, AOP, 필터
 

### 1. 특징
- 요청, 응답 거른 뒤 `정제` 하는 역할
- DispatcherServlet 이전 실행
  - 요청 데이터 / 응답 데이터 확인 및 변경하는 처리 가능
- `WebApplicationContext` 기능 >> Spring 과 무관하게 동작
- 주로 애플리케이션 비즈니스 로직과 관계없는 작업 처리
  - 인코딩 변환 처리, XSS 방어, CORS, LOG 처리
### 2. 주요 메서드
- init(): 필터 인스턴스 초기화 시 실행되는 메서드
- doFilter(): 클라이언트의 요청/응답 처리 시 실행되는 메서드
- destory(): 필터 인스턴스가 제거될 때 실행되는 메서드
### 3. 필터 작성
1. 설정 파일 빈 구현
2. @WebFilter 어노테이션 활용

### 4. 필터 동작 과정
> [참고자료](https://emgc.tistory.com/125)
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/ebfefbc1-9792-48d4-99c1-41664d4853fc)
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/bd9dc16f-b5d7-4787-ba12-ee7dca259a00)

### 5. 2가지 종류의 필터
#### 5-1. Filter인터페이스의 doFilter를 직접 구현한 필터
#### 5-2. Filter인터페이스의 doFilter를 구현한 필터클래스를 상속하여 doFilterInternal을 구현한 필터

