## application context
> [참고자료](https://mangkyu.tistory.com/151)

### 1. 애플리케이션 컨텍스트
- `bean factory` 빈의 생성 & 관계설정 같은 제어 담당하는 IoC 컨테이너
  - 이외 추가적인 기능 >> 빈 팩토리 상속받아 확장한 `application context` 주로 사용!
- `application context`: 생성 정보 & 연관관계 정보에 대한 설정 읽어 처리

### ✔ `Bean` 요청 시 처리 과정
1. `@Configuration` 붙은 클래스들 설정 정보 등록 / `@Bean` 붙은 메소드의 이름으로 빈 목록 생성
2. 클라이언트 해당 빈 요청
3. `application context` >> 자신의 빈 목록에 요청한 이름 있는지 찾음
4. `application context` >> 설정 클래스로부터 빈 생성 요청 및 생성된 빈 돌려줌

#### 요약
- `@Configuration` 붙은 클래스 >> 설정 정보 등록
- `@Bean` 붙은 메소드의 이름으로 빈 목록 생성
