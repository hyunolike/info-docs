## `PropertySourcesPlaceholderConfigurer`
- 프로퍼티 지정
- 추상 클래스 `PlaceholderConfigurerSupprot`를 구현한 클래스
- `PropertySource` 추가해 __@Value__ 어노테이션의 `${...}` 부분에 프로퍼티 값 주입
- `Bean` 으로 등록해 사용 >> `PropertySource`를 여러개 등록 가능
- 프로퍼티 겹칠 땐 먼저 등록된것이 우선!
- 기본은 파일의 값이 로컬 설정보다 우선순위 높다. 로컬 설정을 높게 하려면 설정 바꿔야됨



---
## 용어 정리
- `System.getProperty()`: 시스템의 정보 가져옴
  - 특정 문자를 넣으면 그 값이 `String` 으로 출력!
- `ClassPathResource 클래스`: `CLASS_PATH` 저장된 리소스 파일 쉽게 가져올수 있도록 해줌
