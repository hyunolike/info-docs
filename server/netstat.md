## `netstat`
> 네트워크 상태 확인 방법

- 네트웤 접속, 라우팅 테이블, 네트워크 인터페이스의 통계 정보 보여주는 도구
- 사용 방법: `netstat [옵션] [|grep 포트 번호 or 서비스 명]
- 자주 사용하는 명령어
  - `netstat -ano`: 현재 포트 상태, PID 등 확인

|option|설명|
|-------|-----|
|`-l`(listen)|연결 가능한 상태|
|`-n`(number port)|포트 번호|
|`-t`(tcp)|tcp|
|`-u`(udp)|udp|
|`-p`|프로그램 이름 / PID|
|`-a`|모두|
|`-i`|이더넷 카드별 정상/에러/드랍 송수신 패킷 수 확인|
|`-r`|라우팅 테이블|
|`-s`|네트워크 통계|


![image](https://user-images.githubusercontent.com/61215550/172325434-2ed52642-a644-4433-b118-9e1bb6ec0242.png)

