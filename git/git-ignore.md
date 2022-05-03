## 파일 관리 목록에서 제외 `.gitignore`
> [참고 자료](https://thebook.io/080212/ch03/05/01/)
- 깃은 `tracked` 상태인 모든 것을 추적 관리
- 파일뿐 아니라 서브 폴더와 그 안의 파일들도 포함
- ✔ 즉, 모든 디렉터리 전체가 모두 관리 대상! 
- ✔ 자신의 저장소를 다른 사람들과 공유한다면 이 파일들은 분리해서 관리
- 깃으로 관리하고 싶지 않은 파일과 폴더는 별도의 `.gitignore` 설정 파일 안에 나열!!

### `.gitingore`
- `.` 이 있어 __숨겨진 파일__ 로 관리
- 작성할 때 __저장소 폴더의 최상위 디렉터리__ 에 위치

### `.gitignore` 파일 표기법
- `#` 으로 시작하는 줄은 주석 처리
- 애스터리스크 `*` 기호 사용해 패턴 정의 가능 / 기호는 모든 문자열을 대체
  - `*.obj`
- 제외하지 않는 파일과 필요한 파일은 느낌표 `!` 사용
```
# 환경 설정 파일은 제외하면 안됨
!config.php 
```
- 깃에서 디렉터리 표현할 때 리눅스와 같이 `/` 기호 사용
  - 깃은 glob 패턴을 지원하기 때문에 정규 표현식을 응용하여 작성 규칙을 넣을 수도 있습니다.