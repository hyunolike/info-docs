## `gradle build`
> [gradle 참고 자료](https://mkil.tistory.com/479)
- `gradle clean`: build 디렉토리 반복해서 파일 생성 >> 이전에 생성된 파일과 중복되지 않도록 파일 삭제 후 컴파일 시 ✔ 디렉토리 내용을 한번 싹 지우고 새로 빌드 가능
### `gradle clean build` - TEST 진행 ⭕
- `build`: Base Plugin 기여한 생명 주기 작업
  - 모든 테스트 실행, 프로덕션 아티팩트 생성 및 문서 생성을 포함해 모든 것 빌드
### `gradle clean bootjar` - TEST 진행 ❌
- `bootjar`: Spring Boot Gradle 플러그인에 의해 추가된 특정 작업 >> 생명 주기 작업 java 연결 
  - `jar` 빌드에만 집중! 테스트, 코드 적용 범위, 정적 코드 분석 또는 생명 주기 작업에 첨부도니 모든 실행에는 관심 없는 경우 사용
