## `Spring Boot` + `Chatting Server`
- 크게 2가지 경우
  - Web Socket Server 1개인 경우(`Spring WebSocket`)
  - Web Socket Server 2개인 경우(`STOMP` `Redis Pub/Sub` `세션정보를 아는 또다른 서버 구축`)

### Web Socket Server `1개인 경우`
- ![image](https://user-images.githubusercontent.com/61215550/172735806-9cb1e794-9172-4586-b3cd-0cac5c165f9e.png)
- ![image](https://user-images.githubusercontent.com/61215550/172736435-d7276629-74fd-4e70-bbd7-73f5f0b870dc.png)

### Web Socket Server `2개인 경우`
- ![image](https://user-images.githubusercontent.com/61215550/172736813-bdc03169-cda4-4d98-ae9f-038f0dee7486.png)
- ![image](https://user-images.githubusercontent.com/61215550/172738343-75ffd95e-6f37-4e8e-b3d1-58ff7989a2e0.png)
