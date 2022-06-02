## `gradle` vs `gradlew
> [참고 자료](https://tomgregory.com/gradle-vs-gradlew-difference/)
### `gradle`
- Gradle 설치 후, 환경변수 추가해야 사용 가능

### `gradlew`
- gradle wrapper
- 프로젝트 내에서 패키지로 제공되는 스크립트
- 버전 제어에 커밋되므로 프로젝트 복제 시 >> gradlew 스크립트 자동으로 가져옴
- 장점
  - gradle 로컬 설치할 필요 없다. >> 로컬 gradle에 의존하지 않음. 
  - 고정 버전 >> 특정 gradle 버전과 연결 
