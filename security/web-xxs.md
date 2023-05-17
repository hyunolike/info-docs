## XSS(Cross Site Scripting)
> [참고자료](https://kevinthegrey.tistory.com/36)
- 사이트를 교차해서 스크립트 발생시킴
- 게시판 포함한 웹 >> 스크립트 언어 삽입 >> 개발자 의도하지 않은 기능 작동시키는 것

### 공격 방법
- ✔stored XSS
  - 스크립트 저장해뒀다 공격하는 방법
- ✔reflected XSS
  - 스크립트 입력하면 바로 반사되어 바로 실행하는 방법
### 취약점
- zero board 취약점
  - 웹 해킹 >> 소스코드 보기

### 고전적 보안기법
- 방화벽, IDS, IPS, UTM 같은 장비(보안 솔루션)
- 백신
- 보안패치
- 서드파티 보안

### ✔ 시큐어코딩
- 입력값 html 코드를 검사

