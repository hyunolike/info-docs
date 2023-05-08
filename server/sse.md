## SSE
> Server Sent Event <br>
> [참고자료](https://surviveasdev.tistory.com/entry/%EC%9B%B9%EC%86%8C%EC%BC%93-%EA%B3%BC-SSEServer-Sent-Event-%EC%B0%A8%EC%9D%B4%EC%A0%90-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B3%A0-%EC%82%AC%EC%9A%A9%ED%95%B4%EB%B3%B4%EA%B8%B0)
- Socket: `양방향` 데이터 주고 받음
- SSE: 클라이언트 >> 데이터 받을 수만 있음

### 🪂 Socket vs Server-Sent-Event
||Socket|Server-Sent-Event|
|--|--|--|
|브라우저 지원|대부분 브라우저 지원|대부분 모던 브라우저 지원|
|통신 방향|양방향|단방향(서버 -> 클라이언트|
|리얼 타임|Yes|Yes|
|데이터 형태|Binaary, UTF-8|UTF-8|
|자동 재접속|No|Yes(3초마다 재시도)|
|최대 동시 접속 수|브라우저 연결 한도 없음 / 서버 셋업에 따라 다름|HTTP >> 브라우저당 6개까지 가능 / HTTP2 >> 100개 기본|
|프로토콜|websocket|HTTP|
|베터리 소모량|큼|작음|
|Firewall 친화적|Nope|Yes|

### 사용처
#### 1. websocket
> 주로 리얼타임 필요한 곳에 사용
- 카카오톡
- 주식 트레이딩 데이터
- 크립토 실시간 차트

#### 2. SSE
- 페이스북 친추 요청
  - 클라이언트 데이터만 받기만 하면 됨!
