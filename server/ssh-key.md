## `SSH Key` 비밀번호 없이 로그인
> [참고 자료](https://opentutorials.org/module/432/3742)
- 서버에 접속 할 때 비밀번호 대신 키 제출하는 방식
- SSH key 언제 사용??
  - 비밀번호 보다 높은 수준의 보안을 필요로 할 때
  - 로그인 없이 자동으로 서버에 접속 할 때

### 동작 방식
- ![image](https://user-images.githubusercontent.com/61215550/172992860-996b435e-be1d-4d8e-9e9d-00358243610e.png)
- SSH key의 구성 >> 공개키 + 비밀키
- 키 생성
  - Unix 계열: `ssh-keygen` 프로그램 사용
  - Window: `SSH Client` 프로그램 내 자체적으로 제공하는 키 생성 프로그램
- 키 추가
  - SSH Server 내 `authorized_keys` 파일 추가(공개키)
