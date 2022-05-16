## `docker client` `docker server`
- ![image](https://user-images.githubusercontent.com/61215550/168513196-ee848082-0708-44f3-b7df-e5ba7392d06c.png)
- 도커는 클라이언트, 서버로 나뉘며 그 사이는 `REST API` 로 통신한다
- `client`: 요청만 할뿐 >> build, run, push 등은 실질적으로 ⭐데몬(SERVER) 에서 수행!

### 1. `Docker` 클라이언트
- 일반적으로 우리가 치는 docker 명령어 주인
- `CLI` 명령행 인터페이스
- Docker 서버(데몬)과 대화하려고 노력!

### 2. `Docker` 데몬 - dockerd
- 지속적으로 `running` 되면서 docker cli의 요청을 기다리고 docker 프로세스 관리
- 데몬 >> docker를 관리하기 위해 다른 데몬과 통신 가능

### 3. Docker 통신 방법✔
- Dokcer 데몬과 클라이언트간의 통신 할 때 로컬에서는 `유닉스 소켓` 사용
- 원격에서는 `TCP 소켓` 사용
- `HTTP REST` 형식으로 API 구현⭐
- ![image](https://user-images.githubusercontent.com/61215550/168513875-99ea400c-cb45-4346-abee-f38afa3e9712.png)

