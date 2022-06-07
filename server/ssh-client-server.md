## `SSH` client vs server 
- ssh >> client + server 구성
- ssh 프로토콜 이용해 클라이언트가 명령내리고 서버가 명령받아 컴퓨터 제어
### 제어의 주체 `SSH Client`
- 윈도우 지원 x
  - `Xshell` `Putty` 프로그램 통해 다른 컴퓨터 접속 가능
- 리눅스, 맥은 기본적으로 설치

### 제어의 대상 `SSH Server`
- SSH는 __Unix 계열의 운영체제를__ 원격에서 제어하기 위한 방법 ⭐
- 원격지에 있는 윈도우 운영체제를 SSH로 제어하는 것은 일반적이지 않다. ✔
- 윈도우는 단지 `SSH Client`로 사용할 수 있을 뿐
- 유닉스 운영체제에서 SSH Server로 가장 많이 사용하는 것 `OpenSSH`
  - 맥은 기본적으로 설치 / 리눅스는 별도 설치 필요


