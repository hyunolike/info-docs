## `Web Server` `WAS`
> [참고자료](https://gmlwjd9405.github.io/2018/10/27/webserver-vs-was.html)

### 구분 이유
- Web Server
  - 정적 컨텐츠만 처리하도록 기능을 분배하여 서버의 부담 줄일수 있음
- WAS
  - 요청에 맞는 데이터를 db에서 가져와서 비즈니스 로직에 맞게 그때 그때 결과를 만들어서 제공 >> 자원 효율적 사용 
### `WAS`가 Web Server 기능까지 모두 수행하지 않는 이유? 
> 📌 자원 이용의 효율성 및 장애 극복, 배포 및 유지보수의 편의성 위헤 따로 사용!
1. 기능 분리 >> 서버 부하 방지
2. 물리적으로 분리하여 보안 강화
  - SSL 암복호화 처리 >> Web Server 사용
4. 여러 대의 was 연결 가능
  - Load Balancing 위해 Web Server 사용
  - fail over(장애 극복), fail back 처리 유리
  - 여러 개의 서버 사용 시 >> Web Server + WAS 분리 >> 무중단 운영을 위한 장애 극복 쉽게 대응 가능 
  - 예. 앞단 Web Server에서 오류 발생한 WAS를 이용하지 못하도록 한 후, WAS 재시작 함으로써 사용자는 오류 느끼지 못하고 이용 가능해짐!
5. 여러 웹 애플리케이션 서비스 가능
  - 하나의 서버(PHP + JAVA)
6. 기타
  - 접근 허용 IP 관리 / 2대 이상의 서버에서의 세션 관리 등 Web Server에서 처리하면 효율적
 
### Web Service Architecture
- 3가지 구조
  - Client > Web Server > DB
  - Client > WAS > DB
  - Client > Web Server > WAS > DB
- ![image](https://user-images.githubusercontent.com/61215550/186040087-a404d8f7-bab0-4b2a-865c-e45839d07819.png)
