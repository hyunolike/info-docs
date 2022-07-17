## IPC
> [참고자료](https://blog.container-solutions.com/wtf-is-inter-process-communication)
![image](https://user-images.githubusercontent.com/61215550/179383054-8aa8cffe-ebd5-4987-ae4e-b809e2217374.png)

- 프로세스 간 통신
  - 서비스간 통신(ISC)라고도 하는 IPC(프로세스간 통신)
- 마이크로 커널의 디자인 프로세스에 매우 중요!
- ![image](https://user-images.githubusercontent.com/61215550/177917846-5cf794eb-dcde-49b2-8d3f-e163c976527a.png)

### 1. IPC 방식
- 파일
- 신호
- 소켓
- 메시지 큐
- 파이프
- 지명 파이프
- 세마포어
- 공유 메모리
- 메시지 전달(비공유) >> `RabbitMQ` `Apache Kafka`
- 메모리 맵 파일

### 2. 특징별 기술
#### 2.1 동기 또는 비동기 Synchronous or asynchronous
#### 2.2 Point-to-point or multipotin
- Point-to-point(1 : 1): 요청/응답 통신 / 단순한 비동기식 단방향 알림 이동
- Multipotion(1:n): `publish/subscribe` / 메시지 브로커
  - 메시지 브로커: 여러 서비스에서 처리하기 위해 요청 1번만 하게 됨!!! ✔ `RabbitMQ` `Apache Kafka` / `MQ`
#### 2.3 Message formats
- 사람들 읽고 확인 가능: `JSON` `XML`
- 이진 형식: `protocol buffers` `Apache Avro`

### 3. API의 역할 ⭐
- 일반적으로 서비스 간 또는 서비스와 클라이언트 간의 **계약 역할**
- ![image](https://user-images.githubusercontent.com/61215550/179383295-285273b8-8cf5-4bc6-a267-febd27aa25f0.png)

### 4. REST
- 서비스와 통신하는 사실상의 업계 표준
- Using REST has a few advantages ✔ 이점
  - Simple interfaces, easy to get started
  - Well known and mature
  - Firewall friendly(as it is using the HTTP/S ports) 
  - Testing with a browser or simple curl commands
- There are a few drawbacks as well ✔ 단점
  - Usually synchronous request/response interactions >> Alternative: `messaging`
  - URIs must be known by clients / requires service discovery
  - Endpoints are defined by resources, making it difficult to get data from multiple `GET /customers/customer_id?expand-orders` when trying to get both a customer and an order resource >> Alternative: `GraphQL`
  - No intermediate buffer, so both the requesting and responding services need to be running during the exchange

### 5. GraphQL

### 6. gRPC

### 7. Messaging
- `REST` `RPC` >> 대용량 데이터, 높은 처리량 적합하지 않음 ✔
  -  `RabbitMQ` `Apache Kafka`
