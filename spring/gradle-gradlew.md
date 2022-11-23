## `gradle` vs `gradlew` - updated by `2022/11/23`
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

### (추가) gradle wrapper
> [참고자료](https://velog.io/@hwany/gradle)
- 이미 존재하는 프로젝트를 새로운 환경에 설치 시 >> 설치나 설정과정없이 곧바로 빌드 가능!
  - ⭐자바, 그레들 설치 필요 x / 로컬에 설치된 자바, 그레들 버전 신경 x / 항상 `wrapper` 사용할 것 권장
- `wrapper`: 그레들 설치 x >> Gradle tasks 실행할 수 있도록 해주는 작은 script, jar 및 정보 파일
- wrapper 생성 시, 사용자가 프로젝트를 만든 사람과 동일한 버전의 Gradle 사용 가능

