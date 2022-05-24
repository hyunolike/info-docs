## 외부설정
- 외부 설정 통해 같은 소스코드로 각기 다른 환경에서 실행가능하도록 해줌
- 코드 외부 설정
  - `properties` 파일
  - `YAML` 파일
  - 환경변수
  - 커맨드라인 아규먼트 등...

### 외부설정 소스코드 사용처
- `@Value`: 소스코드에서 바로 프로퍼티 주입받아 사용
- `Environment`: 외부설정이 바인딩 된 Environment를 주입받아 사용
- `@ConfigurationProperties`: 외부설정이 바인딩 될 Bean(객체) 생성해 사용

#### 위에 이들 사이에도 우선순위 존재
- [공식 문서](https://docs.spring.io/spring-boot/docs/2.2.2.RELEASE/reference/html/spring-boot-features.html#boot-features-external-config)
- ![image](https://user-images.githubusercontent.com/61215550/169971300-6af0aaed-102f-498a-bae3-eaca58525032.png)

### 요약
- 스프링부트는 코드 밖에서 외부 프로퍼티 설정 가능
- 외부는 ... 이며 우선순위 존재해 프로퍼티 값 오버라이드 가능
- 외부설정 중 많이 쓰이는 __파일 외부설정__ 은 파일이 위치하는 경로에 따라 우선순위 존재해 프로퍼티 값 오버라이드
- 파일 외부설정시 디폴트 파일명, 경로 외에 spring.config.name, spring.config.location 프로퍼티 설정으로 커스텀한 파일명 또는 경로를 지정할 수 있다.
