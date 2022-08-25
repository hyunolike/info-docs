## Bean 객체 등록 방법
> [참고자료](https://cbw1030.tistory.com/54)
- (기본 지식) 스프링 = 경량 컨테이너(객체 생성, 소멸과 같은 Life Cycle 관리 / 스프링 컨테이너로부터 필요한 객체 얻음)
- 스프링 빈 `Bean`: 스프링 컨테이너에서 만들어진 객체
  - 기존 자바 일반 객체와의 차이점 없음! 단지, 스프링 컨테이너에 의해 만들어진거이기 때문
  - 빈 >> 스프링 IoC 컨테이너에 의해 인스턴스화되어 조립 및 관리되는 객체 ✔
  - 빈과 빈사이의 의존성 >> 컨테이너가 사용하는 메타데이터 환경설정에 반영

### 1. 스프링 빈의 어노테이션 종류
- @Component
  - @Service
  - @Controller
  - @Repository
- @Bean
- @Configuration
- @Autowired(주입 사용)

### 2. 사용
#### 2.1 @Component & @Autowired
- 클래스위에 `@Component` 붙으면 스프링 빈 객체로 등록! >> 객체 생성/삭제 스프링에서 관리 가능해짐
- 2개의 빈 사용시 주의점
  - 어떤것이 필요로 하는지 모름...ㅠ,ㅠ(맨 아래 참고)

#### 2.2 @Bean & @Configuration
- 자바 설정 클래스
  - 초기 스프링 기반 개발에서의 빈 생성 >> xml로 된 스프링 설정파일 통해 이뤄짐

### 3. 빈 객체 우선권 부여하기
#### 3.1 @Primary & @Qualifier
- @Primary: @Bean or @Component와 함께 사용 >> 객체 생성의 우선권 부여
- @Qualifier: @Autowired 함께 사용 >> Bean의 이름이 같은 객체 사용

