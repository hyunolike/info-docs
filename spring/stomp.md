## `STOMP` + `WebSocket`
### 1. `WebSocket`
- HTTP처럼 서버 <--> 클라이언트 간 양방향 통신 제공하는 프로토콜
- 다수의 클라이언트 하나의 서버

### 2. `STOMP`(Streaming Text Oriented Messaging Protocol)
- 통신 프로토콜
- 특정 토픽 `subscriber`(구독) / 특정 user에게만 메시지를 보내는 방법을 담당하는 프로토콜
- 프로토콜 지원하는 `Message Broker` + `Client` 간 통신 지원
- Spring은 기본 지원
- 다른 통신 프로토콜 >> `RabbitMQ` `ActiveMQ` 등 사용 가능


