## NAT IP
> [참고자료](https://blog.voidmainvoid.net/319)
- Network Address Translation
- ⭐사설 네트워크에 속한 여러 개의 호스트  >> 하나의 공인 IP 주소를 사용하여 **인터넷** 접속을 위할 목적!!
- ![image](https://user-images.githubusercontent.com/61215550/233896904-1d443a85-3848-48b3-9831-94a2bf19a8ce.png)

### 특징
- 내부에서 외부로 통신 가능 ✔
- 외부에서 내부로 통신 불가

### 장단점
#### 😛 장점
- 여러 사설 네트워크 사용 >> 인터넷 공인 IP 주소 절약 가능
- 사내망 IP주소를 외부로 알리지 않음으로서 외부로부터의 침입/공격 차단
#### 🙄 단점
- 네트워크 복잡성 증가
- 네트워크 지연 영향
### 🛰 NAT 종류
- `Static NAT`: 사설IP + 공인IP 1:1 매핑
- `Dynamic MAT`: 다수 공인 IP: 다수 사설 IP
- `PAT`: 1개의 공인 IP : 다수의 사설 IP >> 1개 공인 IP에 port 구분하여 사설 PC 구분
