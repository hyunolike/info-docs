## npx 란
> [참고자료](https://webruden.tistory.com/275)
- `node` 5.2.0 버전부터 새로 추가
- `npm@5.2.0` 이상부터 사용 가능
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/bb1825eb-068c-47dd-a6f0-dc5584bac169)
### 등장 이유
- 과거 npm 패키지 설치 2가지 케이스
  1. 전역으로 패키지 설치 > 의존성 라이브러리 전체적으로 관리 방법
  2. 특정 프로젝트에만 의존성 라이브러리 설치 방법
- 😛 `npx` > 1회성으로 원하는 패키지를 npm 레지스트리에 접근 및 실행 설치하는 `실행도구`
### 언제 사용
- `npm run-script` 사용 x > 로컬 설치된 패키지 사용하는 경우
- 일회성 명령으로 패키지 실행
- `gist-based scripts` 실행
- 특정 노드 버전의 스크립트 실행하는 경우
