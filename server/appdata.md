## AppData `Windows` - Applicaton Data 의 약자
> [참고자료](https://webdir.tistory.com/549)
- 각각의 윈도우즈 계정에 존재
- 응용 프로그램의 데이터 및 설정 내용 저장
- 숨김 파일 표시하는 경우에만 볼 수 있음! 
- `%APPDATA%` 입력 시 자동으로 `AppData\Roaming` 이동
- `Roaming` `Local` `LocalLow` 3가지 유형 설정 저장!

### 1. Roaming
- 로밍 폴더 >> 컴퓨터와 컴퓨터간에 사용자 계정으로 로밍할 수 있는 데이터 존재!

### 2. Local
- 단일 컴퓨터의 특정한 데이터 저장

### 3. LocalLow
- Local 폴더와 동일
- 제한된 보안 설정으로 실행되는 "low integrity" 응용 프로그램 위해 설계
  - 보호모드 `Protected Mode`에서 실행되는 인터넷 익스플로우는 LocalLow 폴더에만 접근 가능
