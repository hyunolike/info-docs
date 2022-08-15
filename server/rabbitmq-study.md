## RabbitMQ 쓰는 이유~?
- 😛백엔드는 크게 2가지로 나뉜다
  - 앞단(api 서버): `RESTful` `SOAP` `GraphQL` ...
  - 뒷단(Analysis 서버): 데이터 처리, 분석 서버
- ![image](https://user-images.githubusercontent.com/61215550/184623880-232d23f7-8743-4bd0-ab17-2baef477ac3b.png)
- 요약
  - 데이터 쌓아두는 창고, 수틀려도 MQ녀석만 죽어서 서비스는 돌아감
  - AMQP 형식!! >> 그래서 양쪽 서버에 `AMQP` 형식만 맞춰주면 (어뎁터) 잘돌아감
  - 메이저 언어 다 지원해서 각 언어의 장점이 맞는 부분 사용 가능해짐!!
  
### 필요한 이유
|기존|`RabbitMQ` 사용|
|----|------------------|
|![image](https://user-images.githubusercontent.com/61215550/184624045-efde9158-a992-4430-a782-d6e96663764d.png)|![image](https://user-images.githubusercontent.com/61215550/184624065-b04f8571-e39c-44f9-a17d-b35a9f06b605.png) <BR> ![image](https://user-images.githubusercontent.com/61215550/184624095-6d063553-ce7d-4e8b-895f-76a072911187.png)|
