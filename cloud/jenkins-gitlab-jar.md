## `Jenkins` + `Gitlab` >> Jar 파일 자동 배포
> [참고 자료](https://hwannny.tistory.com/108) <br>
> [gitlab + jenkins 참고 자료](https://velog.io/@hmyanghm/Jenkins%EC%97%90-GitLab-%EC%A0%80%EC%9E%A5%EC%86%8C-%EC%97%B0%EB%8F%99)

### 설정 사항
1. Publish Over SSH 설정 및 Jenkins에 접근하고자하는(배포) 서버 등록 ✔ 기본 설정 및 원격 서버 연결
2. 빌드할 Github repository branch 가져오도록 설정 ✔ git 연결 프로젝트 설정
3. 빌드 전 수행 할 내용 설정  ✔ `Pipeline`
4. 빌드 설정 
5. 빌드 후 조치 내용 설정
