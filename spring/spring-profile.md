## `Profile`
> [참고 자료](https://atoz-develop.tistory.com/entry/Spring-EnvironmentCapable-Profile-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0)
- 특정 실행 환경에서 사용할 빈들의 묶음
- 테스트 환경에서 사용할 빈 묶음과 프로덕션(운영) 환경에서 사용할 빈 묶음이 서로 다를 수 있음
- 각 환경에 따라 서로 다른 빈들을 써야하는 경우 / 특정 환경에서만 등록해야하는 빈들이 있는 경우

### `Environment` 역할
- 활성화 할 프로파일 확인 및 설정 

### 프로파일 정의
- `@Profile` >> 클래스, 메서드 붙인다
