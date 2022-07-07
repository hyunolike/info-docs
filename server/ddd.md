## DDD `Domain Driven Design`
> [참고 자료](https://incheol-jung.gitbook.io/docs/q-and-a/architecture/ddd)
### 1. 특징
- 일반적인 데이터 중심의 접근법 탈피해 순수한 도메인의 모델과 로직에 집중
- 보편적인 언어의 사용
- 소프트웨어 엔티티와 도메인 컨셉트를 가능한 가장 가까이 일치시키는 것
#### 1.1 데이터 주도 설계?
- 데이터 초점을 두고 설계하는 방식
- 객체 자신이 포함하고 있는 데이터 조작하는데 필요한 행동
- 아래와 같은 문제점 발생 ㅠ,ㅠ
  - 과도한 getter, setter 생성
  - 캡슐화 원칙 위반
  - 높은 결합도
```java
public class Movie {
    private String title;
    private Duration runningTime;
    private Money fee;
    private List<DiscountCondition> discountConditions;

    private MovieType movieType;
    private Money discountAmount;
    private double discountPercent;

    // getter, setter..
}
```

### 2. 도메인 주도 설계
- MSA에서 도메인 주도 설계 찾는 이유 ✔
  - ![image](https://user-images.githubusercontent.com/61215550/177693713-6c316a85-3a92-44b9-8edc-2cdd3e969fc1.png)
#### 2.1 용어 정리
|용어|설명| 
|-----|-----------------------------------|
|`ubiquitous language`|도메인 사용 용어 사용 >> 코드의 가독성 높이고 이해하는데 시간 절약 / 다른 사람들과의 공통된 언어 사용 가능|
|`Domain`|일반적인 요구사항, 소프트웨어로 해결하고자 하는 문제 영역|
|`Domain Model`|특정 도메인을 개념적으로 표현한 것|
|`Entity`|테이블 모델, 고유 식별자 가짐|
|`Value Object`|데이터 표현 모델 식별자를 가지고 있지 않고 불변 타입|
|`Aggregate`|- 연관된 엔티티와 벨류 오브젝트의 묶음 / 일관성과 트랜잭션, 분산의 단위<br>- 루트 레그리게이트: 에그리게이트가 제공해야 할 핵심 도메인 기능을 보유하고 있는 모델<br>- ![image](https://user-images.githubusercontent.com/61215550/177694385-e649dae4-5a19-4634-bc72-c72418e0ddaf.png)|
|`Bounded Context`|특정한 도메인 모델이 적용되는 제한된 영역 경계 내에선 동일한 모델을 알관되게 적용<br>![image](https://user-images.githubusercontent.com/61215550/177694520-399c5275-702b-43a1-8e10-0bbe066f100d.png)|
|`Context Map`|`Bounded Context` 간 관계<br>![image](https://user-images.githubusercontent.com/61215550/177694595-959c59bf-fba4-4fc9-a3cc-47c798cf7190.png)|

### 3. 이벤트 스토밍
- 도메인 전문가 <--> 개발자 
  - 전략적으로 설계를 효율적으로 할것인가에 대한 방법
 
### 4. 도메인 주도 설계 아키텍처 
- ![image](https://user-images.githubusercontent.com/61215550/177695986-673aae02-8e74-4a16-81f6-e7aa0805d42f.png)
- `DIP`

### 5. Event Driven Design
- 이벤트 관련 구성요소
  - 이벤트 주체: 엔티티, 벨류, 도메인 서비스와 같은 도메인 객체
  - 도메인 객체: 도메인 로직 실행 >> 상태 바뀌면 이벤트 발생
  - 이벤트 핸들러: 이벤트 생성 주체가 발생한 이벤트에 반응
  - 이벤트 디스패처: 이벤트 생성 주체, 이벤트 핸들러 연결
  - 디스패처: 해당 이벤트 처리할 수 있는 핸들러에 이벤트 전파 
- 이벤트 구성
  - 이벤트는 현재 기준으로 과거에 벌어진 것을 표현! >> 이벤트 이름은 __과거 시제__
  - 이벤트는 필요한 최소한의 데이터 담아야됨
- 이벤트 용도
  - 서로 다른 시스템간의 데이터 동기화
- 이벤트 장점
  - 서로 다른 도메인 로직이 섞이는 것을 방지
  - 이벤트 핸들러를 사용하면 기능 확장 용이
- 비동기 이벤트 처리
  - 로컬 핸들러를 비동기로 실행
  - 메시지 큐 사용
  - 이벤트 저장소와 이벤트 포워더 사용
  - 이벤트 저장소와 이벤트 제공 API 사용

### 6. `CQRS` - 명령 및 쿼리 책임 분리
#### 6.1 단일 모델의 단점
- `ORM` 기법은 도메인의 상태 변경 용이 / 여러 애그리거트에서 데이터를 가져와 출력하는 기능을 구현하기에는 고려할 것 많아 구현 복잡 ㅠ,ㅠ
- 해결 방법 >> 상태 변경을 위한 모델과 조회를 위한 모델을 분리하는 것
#### 6.2 CQRS란 
- 상태를 변경하는 명령을 위한 모델과 상태를 제공하는 조회를 위한 모델을 분리하는 패턴
- 복잡한 도메인 적합 

#### 6.3 웹과 CQRS
- 메모리에 캐시하는 데이터는 DB에 보관된 데이터를 그대로 저장하기보단 화면에 맞는 모양으로 변환한 데이터를 캐시할 때 성능에 더 유리
- 조회 속도를 높이기 위해 별도 처리하고 있다면 명시적으로 명령 모델과 조회 모델 구분
- 조회 기능 있기에 명령 모델이 복잡해지는 것 방지 / 명령 모델에 관계없이 조회 기능에 특화된 구현 기법을 보다 쉽게 적용

#### 6.4 장단점
- 명령 모델 구현 시 도메인 자체에 집중
- 조회 성능을 향상시키는데 유리
- 구현해야 할 코드 더 많아짐
- 더 많은 구현 기술 필요
- ![image](https://user-images.githubusercontent.com/61215550/177697949-e30233ac-3026-4e97-9ed2-234a68042911.png)

