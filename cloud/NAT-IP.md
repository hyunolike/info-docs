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

## NAT (Network Address Transaction) 추가 업데이트 내용
> [참고자료](https://blog.naver.com/skyhomo/220049937649)
- 사설 ip 주소 > 공인 ip 주소 바꾸주는데 사용하는 통신망의 `주소 변환기`
- 2가지 유형
  - `Static NAT`
  - `Dynamic NAT`

## 사용 이유
> [참고자료](https://isaac56.github.io/network/2021/01/07/NAT/)
- 여러 대의 기기들을 > 하나의 로컬 망 묶어
- 로컬 망 내 사설 ip를 공인 ip로 맵핑
- ⭐보안&IPv4 주소 고갈 문제 대응책
- 내부에서 외부로 나간 패킷이 다시 돌아오게 하기 위한 기능

## 추가 설명
> [참고자료](https://onlythisone.tistory.com/entry/NAT-Static-NAT)
>> ![image](https://github.com/hyunolike/info-docs/assets/61215550/38bca040-8fd4-462e-a026-f415d1e29855)
- ⭐`사설ip`: 부족한 공인ip 대신해 사용하는 일종의 `복사본 ip`

