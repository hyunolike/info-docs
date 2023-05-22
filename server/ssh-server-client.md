## ssh server <--> ssh client
> [참고자료](https://velog.io/@lehdqlsl/SSH-%EA%B3%B5%EA%B0%9C%ED%82%A4-%EC%95%94%ED%98%B8%ED%99%94-%EB%B0%A9%EC%8B%9D-%EC%A0%91%EC%86%8D-%EC%9B%90%EB%A6%AC-i7rrv4de)
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/aabea273-2b0d-46bd-be3e-611dc8deef13)
### SSH 공개키 접속 방법
#### 1. SSH 클라이언트 `사용자`
- 클라이언트 키 쌍
  - `ssh-keygen` 명령어 사용
  - `~/.ssh/known_hosts` 파일 >> 사용자 처음 로그인 / 연결 진행 >> **서버의 공개키** 해당 파일에 기록!
#### 2. SSH 서버 `호스트`
- 서버 키 쌍
  - 서버 `openssh-server` 설치하는 과정에서 자동 생성
  - 클라이언트 서버 처음 접속 >> 해당 공개키 클라이언트에게 제공
  - 클라이언트 `known_hosts` 파일에 기록
- `~/.ssh/authorized_keys` 파일
  - 로그인할 클라이언트 공개키 기록!! (중요)⭐

#### 3. 공개키 접속
1. 클라이언트 키 쌍 생성
2. 공개키 전송
3. 로그인
4. 키 파일 권한 문제
  - ![image](https://github.com/hyunolike/info-docs/assets/61215550/9616ee19-0479-4209-9744-41b04cec2c96)
