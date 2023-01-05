## SSH Tunneling
> [참고자료](https://hbase.tistory.com/328)
- ![image](https://user-images.githubusercontent.com/61215550/210720037-833ea625-187d-4d84-b4d1-410fb20c2fa1.png)


- `sh`: `Secure SHell` 줄임말 / 원격 호스트 접속하기 위해 사용되는 보안 프로토콜
- ssh >> 원격 호스트로의 접속 + `ssh tunneling`/`ssh port forwarding`

### 1. SSH Tunneling (SSH Port Forwarding)
- 프록시와 비슷한 역할 수행


|기존|`SSH Tunneling`|
|---|-----|
|![image](https://user-images.githubusercontent.com/61215550/210717292-f3ae75a4-9f21-4516-8788-2ecee74b0b9c.png)|![image](https://user-images.githubusercontent.com/61215550/210717316-79d3f865-7751-4ec1-9c84-16997142f9e0.png)|


### 2. 종류 3가지
> 방화벽 우회 접근 가능 ⭐
- Local Port Forwarding
- Remote Port Forwarding
- Dynamic Port Forwarding

### 3. 구성 방법
- 보안상 문제 >> ssh 서버 허용 불가

---
### 1. Local Tunneling (Local Port Forwarding)
![image](https://user-images.githubusercontent.com/61215550/210718167-eb218b66-98dc-42ac-8ecd-b8f3c3bac3bd.png)

### 2. Remote Tunneling (Remote Port Forwarding)
- ✔ 외부에서 서버로 들어오는 연결을 모두 막아둔 경우


|기존|개선|
|---|----|
|![image](https://user-images.githubusercontent.com/61215550/210718718-b5fc212c-630a-4b67-955a-c46df2c4d84c.png)|![image](https://user-images.githubusercontent.com/61215550/210718746-c2c3d007-f79e-4bec-af8c-b35ac350ee64.png)|


### ⭐ ssh 터널링 장단점
- 방화벽 우회 >> 장점ㅋㅋㅋㅋ
- 방화벽 왜 쓰는지 확인 !! >> 단점 ...
  - 대규모 트래픽 처리하려는 경우 쓰지마
