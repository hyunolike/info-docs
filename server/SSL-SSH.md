## `SSL` `SSH`
- SSH: 암호화된 통신(서버간)
- SSL: 암호화 기반 인터넷 보안 프로토콜
### 1. `SSH`
> `HTTPS`: 통신 간 데이터 암호화
- SSH 통해 원격 컴퓨터 제어하기 위해서 2가지 충족
  1. Client >> ssh client 프로그램 설치
  2. Server >> ssh server 프로그램 설치
  3. 각 ssh 프로그램 간 커넥션 맺어질 수 있어야 됨
#### 1-1. 장점
- 암호화된 통신
  - client <-> host(서버) 간 통신 암호화
#### 1-2. Encryption/Decryption 과정
- 데이터 암호화 3가지
  - 대칭 암호화
  - 비대칭 암호화
  - 해쉬함수
- 대칭 암호화✔
  - 1개의 공통된 `Secret Key` 갖고 양쪽에서 데이터 암호화 및 복호화할 수 있게 하는 방법
  - ![image](https://user-images.githubusercontent.com/61215550/171085740-be257754-817e-4c2c-9f1f-5c0d3f617fec.png)
- 비대칭 암호화✔
  - ![image](https://user-images.githubusercontent.com/61215550/171085839-1c6a055a-6206-4670-a4ff-51fa01f1634a.png)
- 해쉬 함수✔
  - ssh 커넥션 성공되기전 위장해 모든 정보 조작할 가능성 존재
```
Hash 함수가 전송되는 메시지, 송/수신자가 공유하는 Secret Key, 그리고 Packet Sequence Number를 가지고 MAC 값을 출력하여 수신자(Host)에게 보내줍니다. 
수신자도 같은 정보를 가지고 있기 때문에, 같은 정보를 가지고 똑같은 Hash 함수를 돌려 나온 MAC 값이 일치하는지 확인하는 방식입니다.

Hashing은 기본적으로 단방향으로 이루어집니다. 단방향으로 이루어지는 이유는 복호화를 염두에 두고 사용하는 암호화 과정이 아니기 때문입니다.
```

#### 1-3. Authentication
- ssh 인증 방식 2가지
  - Password(username/password - username은 보통 root)
  - RSA(password 없이 identity 확인)
- `RSA`
  - 내 컴퓨터에 SSH 키 생성 >> 나의 public key를 host의 인가 목록에 추가해 자동으로 나를 인증하는 방식
  - 비밀번호 없이 인증 가능

### 2. `SSL`
> [참고 자료](https://www.cloudflare.com/ko-kr/learning/ssl/what-is-ssl/)
- Secure Sockets Layer
- 현재 사용 중인 TLS 암호화의 전신
- SSL/TLS 사용하는 웹사이트의 URL >> `HTTPS`
