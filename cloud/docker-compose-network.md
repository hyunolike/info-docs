## `Docker Compose` 네트워크
> [참고 자료](https://www.daleseo.com/docker-compose-networks/)
- 기본적으로 하나의 디폴트 네트워크에 모든 컨테이너 연결
  - 디폴트 네트워크의 이름 `docker-compose.yml` 위치한 디렉토리 이름 뒤에 `_default` 붙는다.
  - 예) `out_app` 이라면 >> `our_app_default` 생성
- 컴포즈는 먼저 네트워크 생성 후 각 컨테이너 구동

### 커스텀 네트워크 추가
```yml
services:
  web:
    build: .
    ports:
      - "8000:8000"
    networks: ✔
      - default
      - our_net

```
- 디폴트 네트워크 뿐만 아니라 다른 네트워크도 필요에 따라 추가 가능

### 외부 네트워크 사용
- 미리 생성해놓은 다른 네트워크 사용 가능
- ✔ 외부 네트워크 잘 활용되면 서로 다른 Docker Compose에서 돌아가고 있는 컨테이너 간에도 연결 가능해짐!
- ![image](https://user-images.githubusercontent.com/61215550/167339812-55a75f05-675b-42cc-9f48-74ab1bc2e65b.png)

```yml
networks:
  default:
    external:
      name: our_net ✔ 미래 생성해야되는 전제조건
```
