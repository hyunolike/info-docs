## sudoers 수정해서 sudo 권한 부여하기
> [참고 자료](https://projooni.tistory.com/entry/%EB%A6%AC%EB%88%85%EC%8A%A4ubuntu%EC%97%90%EC%84%9C-sudoers-%EC%88%98%EC%A0%95%ED%95%B4%EC%84%9C-sudo-%EA%B6%8C%ED%95%9C-%EB%B6%80%EC%97%AC%ED%95%98%EA%B8%B0)
- `sudo`: 일반 사용자에게 임시적으로 `root` 권한 주는 프로그램 / `superuser do`에서 유래
  - 명령어 앞에 sudo 붙이면 root 권한 실행하겠다는 의미

### `sudoer` 파일 수정
1. 먼저 root 계정 변경 `sudo su`
2. `sudoers` 파일 열기 `vi /etc/sudoers`
3. 계정과 옵션 입력
  - 파일 중간 `root ALL=(ALL:ALL) ALL` 부분 라인 확인
  - 그 밑에 신규 계정 추가 `유저명 ALL=(ALL:ALL) NOPASSWD:ALL`
  - 여기서 `NOPASSWD` 실행할때마다 패스워드 묻지 않겠다는 뜻
- ![image](https://user-images.githubusercontent.com/61215550/173014843-4b4a9742-a8ca-4107-8680-eb948f5b2e9a.png)
