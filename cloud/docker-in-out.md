## `docker in docker ` `docker out of docker`
> [참고 자료](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=isc0304&logNo=222274955992)
- 도커 사용해 컨테이너에서 컨테이너 실행하기
- 크게 2가지
  1. Docker in Docker `DinD`
  2. Docker out of Docker `DooD`

### `Docker in Docker`
- 도커 컨테이너 내에서 도커 데몬 추가 동작
  - 실제 데몬 동작하기에 추가 권한 필요 `--privileged`
- 보안상 문제로 추천하지 않음!

### `Docker out of Docker`
- 내부에 컨테이너를 만들지 않고 기존에 사용하던 컨테이너를 추가로 생성

## Docker의 Client-Server 아키텍처 ✔
> [참고 자료](https://aidanbae.github.io/code/docker/dinddood/)

- ![image](https://user-images.githubusercontent.com/61215550/168505833-15311d5a-dacb-42d2-b68c-3ea266875c3e.png)
- docker 시스템 유닛 3가지
  - `Client` `Host(Daemon)` `Registry`
- Docker daemon
  - API 요청 수신 및 이미지, 컨테이너, 네트워크 및 볼륨과 같은 Docker 객체 관리 
- Docker client
  - `docker run` 과 같은 명령 사용
- Docker registries
  - Docker 이미지 저장 



