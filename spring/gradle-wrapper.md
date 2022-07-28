## Gradle Wrapper
> [참고자료](https://jungseob86.tistory.com/21)

- Gradle 빌드 권장 방법 
- `Wrapper`: 미리 선언된 버전의 Gradle 호출 >> 필요한 경우 미리 다운로드
- ✔ CI 환경 프로젝트 빌드 환경과 매번 맞춰줄 필요 없는 이유 >> `Gradle Wrapper` 사용하기 때문!
  - 환경에 종속되지 않고 프로젝트 빌드 가능

### 구조
- `gradlew.bat`: 윈도우용 wrapper 실행 스크립트
- `gradlew`: 유닉스용 wrapper 실행 스크립트 / 컴파일, 빌드 등을 하는 경우 >> `./gradlew {task}` 형태로 실행
- `gradle/wrapper/gradle-wrapper.jar`
  - Wrapper 파일 
  - 실행 스크립트 동작 >> Wrappe에 맞는 환경을 로컬 캐시에 다운로드 받은 뒤에 실제 명령에 해당하는 task 실행
- `gradle/wrapper/gradle-wrapper.properties`
  - Gradle Wrapper 설정파일
