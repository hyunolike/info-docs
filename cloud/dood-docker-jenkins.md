## `DooD` 젠킨스 컨테이너에서 도커 사용
> [참고 자료](https://bitgadak.tistory.com/3)
- `DooD`: 도커와 소켓을 공유해서 사용
  - `DinD`는 공식 도커에서도 추천하지 않다고 나옴✔
- `DooD`의 컨테이너 격리 문제
  - 컨테이너 이름 충돌
  - 마운트 경로 > 호스트 파일 경로 기준으로 설정
  - 포트 맵핑 > 맵핑은 호스트 레벨에서 하기 때문에 포트 충돌 가능성
### 구조
- ![image](https://user-images.githubusercontent.com/61215550/168514444-0dd2dcc4-d4f3-4fb3-8a6f-7b9710fae1d1.png)
- 호스트 서버
- 젠킨스 컨테이너

### 핵심
- `docker.sock` 마운트 > 호스트의 도커 소켓을 컨테이너에 마운트!
  - 이를 통해 컨테이너 내부에서 외부(호스트)의 docker 서버에 접근 가능
  - `docker run -it -v /var/run/docker.sock:/var/run/docker.sock docker` 
---
### 용어 정리
- `container`: 마치 __별도의 서버__ 인 것처럼 사용할 수 있게 만든것!


