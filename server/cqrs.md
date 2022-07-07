## `CQRS` Pattern
> [참고 자료](https://always-kimkim.tistory.com/entry/cqrs-pattern) <br>
> [명령 및 쿼리 역할 구분 CQRS](http://www.msaschool.io/operation/integration/integration-six/)
- Command Query Responsibility Segregation(명령 조회 책임 분리)
  - `Command`: Create - Insert, Update, Delete >> 데이터를 변경 ⭐
  - `Query`: Select - Read >> 데이터 조회 ⭐
- 애플리케이션 구현하면서 `명령` `조회` 에 대한 책임 분리하는 것 ✔
- ![image](https://user-images.githubusercontent.com/61215550/177708427-ede86a66-e557-48d5-9eb0-bf889a26cae3.png)

### 1. 명령, 조회 분리 이유
- ✔ 비즈니스 로직 >> 대부분 변경(CUD)에서 처리
- ✔ 조회(Read)는 단순 데이터 조회가 대부분


|문제점 ㅠ,ㅠ|해결|적용 모습!!!!|
|-------------|--------------|-----|
|![image](https://user-images.githubusercontent.com/61215550/177707383-e5580ccc-b150-4885-9970-d8fb87d52895.png)<BR>![image](https://user-images.githubusercontent.com/61215550/177710774-19ec39f1-8032-49a7-b42c-ce6c2ee60411.png)|![image](https://user-images.githubusercontent.com/61215550/177707410-6dfb6673-8c6a-4348-aeb7-3f08f961c8ad.png)|![image](https://user-images.githubusercontent.com/61215550/177709537-d200d7f1-9bb4-42f0-968b-b48704fb1f54.png)|


### 2. 어떻게 구현
- 이벤트 혀앹로 구현된 프로그래밍 모델
- `Event Sourcing`
- `Eventual Consistency`
- `Domain Driven Design`
- ![image](https://user-images.githubusercontent.com/61215550/177708212-8e5cf9d6-4c82-467a-ba7b-2deb95774870.png)
