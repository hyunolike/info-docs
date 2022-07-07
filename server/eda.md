## Event Driven Architecture
> [참고 자료](https://medium.com/dtevangelist/event-driven-microservice-%EB%9E%80-54b4eaf7cc4a)
> <br> [이벤트 기반 분산 시스템을 향한 여정](https://www.slideshare.net/arawnkr/ss-94475606)
- MSA 적용된 시스템 보완

### 1. 개념
> `programming` `architecture` 등과 연결되어 다양한 정의로 표현
- 시스템 내 외부에 발생한 상태의 변화에 기반한 동작
- 분산 처리 시스템과 연결되어 언급도 됨!! >> 분산 처리 시스템 + `Event Driven`: 느슨한 결합 지원하고 유연성, 탄력성, 확장성 있는 시스템 구현 가능
- ✔ 분산된 시스템 간에 이벤트를 생성, 발행하고 발행된 이벤트를 필요로하는 수신자에게 전송
- 이벤트를 수신한 수신자가 이벤트를 처리하는 형태의 시스템 아키텍처

### 2. 구성 요소
- `Event generator`: 시스템 내,외부의 상태 변화를 감지하여 표준화된 형식의 이벤트 생성
- `Event channel`: 이벤트를 필요로 하는 시스템까지 발송
- `Event processing engine`: 수신한 이벤트를 식별, 적절한 처리를 함. 때에 따라 이벤트 처리의 결과로 또 다른 이벤트 발생할 수 있음

### 3. Event Processing Style
> 수신한 이벤트 처리 방법 3가지
- `Simple event processing`
  - 각각의 이벤트가 직접적으로 수행해야할 action과 매핑
  - 실시간으로 작업의 흐름을 처리할 때 사용 / 이벤트 처리 시간과 비용 손실 적음
- `Event Stream Processing`
  - 이벤트를 중요도에 따라 필터링하여 걸러진 이벤트만을 수신자에게 발송
  - 실시간으로 정보의 흐름을 처리할 때 사용 / 기업에 적용될 경우 신속한 의사 결정 가능 `BAM`
- `Complex event processing`
  - 일상적인 이벤트의 패턴을 감지하여 더 복잡한 이벤트의 발생을 추론하는 것
  - 예. __주식의 등락__ 

### 4. 장단점
- ✔장점
  - `Decoupling`: 시스템 간의 느슨한 결합이 가능 하므로 분산 시스템 / MSA 환경에서 시스템 간 의존성 배제할 수 없음
  - 다른 시스템의 정보 알 필요 없음 >> 약속된 __Event message__ 를 가지고 상호 정보를 교환
  - micro service 단위로 시스템 분리하기 쉽기 때문에 확장성, 탄력성 고려하기 쉬움
- ✔단점
  - `Broker Dependency`: Event 전송하기 위한 Message Broker에 대한 의존성 커지기에 / 장애 발생 시, 전체 장애 ㅠ,ㅠ
  - Transaction 단위로 격리 >> 서비스 장애 발생 시 retry/rollback 고려
  - 시스템 전체 Flow 파악 어려움 ㅠ,ㅠ >> 명확한 Flow 보기 위해선 시스템 모니터링
  - 디버깅 어려움 ㅠ,ㅠ
### 5. Event Driven MicroService `EDM`
- ![image](https://user-images.githubusercontent.com/61215550/177700597-82d76d52-de4f-497c-9b7a-a592362ae6ff.png)
- MSA가 적용된 시스템에서 이벤트 발생시 해당 이벤트 로그를 보관하고 이를 기반으로 동작, 비동기 통신을 통해 시스템 내 통합을 수행하는 아키텍처


|용어|설명| 
|------|-------------|
|이벤트|상태의 변경 / 데이터의 변경, 생성, 삭제를 통해 발생하는 서비스의 의미있는 변화|
|이벤트 로그를 보관|- 전제 조건: 현재의 데이터는 상태 변경의 누적<br>- 변경 >> 이벤트 / 누적하는 행위 >> 이벤트 로그 보관<br>- `EDM`에서 생성된 이벤트는 반드시 보관|
|비동기 통신|`AMQP` `MQTT` `JMS` 등 메시징 프로토콜을 통한 메시지 큐 방식 자주 사용 <BR>![image](https://user-images.githubusercontent.com/61215550/177702488-643e41e4-a888-463d-b365-cf05f689e7e7.png)|
|시스템 내 통합|필수!|
