## ip 종류
> [참고자료](https://keykat7.blogspot.com/2020/06/network-ip-portforwarding.html)

### 외부 IP (공인 IP) - 외부 네트워크
> ⭐ 전세계에서 유일
- ✔ 일반적으로 검색해서 나오는 IP >> 인터넷상
- 집에서 다른 외부와 통신할 때 사용하는 IP 

### 내부 IP (사설 IP) - 내부 네트워크
> ⭐ 하나의 네트워크(회사, 사내망, 집) 에서 유일
- ✔ `cmd - ipconfig` 명령어 치면 나오는 IP
- 인터넷 연결이 되지 않기에 외부와 차단된 사설 IP
- 모뎀 >> 인터넷 연결
  - 라우터 & 공유기 >> 사설 IP 생성 >> 내부 네트워크 내의 모든 기기 연결

### 유동 IP
- DHCP
- 인터넷 접속 시 계속 바뀜
- 종류 후 매번 바뀜
- 내부에서 인터넷 접속 용도니까 외부에서 접속할 일 없는 경우

### 고정 IP
- 말 그대로 고정
- 외부로부터의 접속하기위해 사용함!!

### localhost IP
- 자기 자신을 가리키는 IP 주소

---
## ⭐ 공인IP vs 사설IP - [참고자료](https://better-together.tistory.com/124)
> 초기 사설IP >> 인터넷과의 연결 고려하지 않은 네트워크에서만 사용! `NAT` 기술 개발로 가능해짐
- ![image](https://user-images.githubusercontent.com/61215550/224219502-8c1a28a7-218e-4237-bea2-7800ef9f028b.png)
- ![image](https://user-images.githubusercontent.com/61215550/224219793-821c1581-d33b-4895-ad59-208906a7c725.png)
- ![image](https://user-images.githubusercontent.com/61215550/224220347-81a0b960-d183-4ae7-b19e-070db62e9e7c.png)
