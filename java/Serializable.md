## 자바 직렬화
### 직렬화, 역직렬화
> [참고자료](https://kwangkyun-world.tistory.com/entry/Java-%EA%B0%9D%EC%B2%B4-%EC%A7%81%EB%A0%AC%ED%99%94Serialization-%EC%99%80-%EC%97%AD%EC%A7%81%EB%A0%AC%ED%99%94Deserialization)
- 자바 데이터 >> `객체`
- 네트워크
    - 객체(데이터) 그 자체 전송 불가🙄
    - `바이트` 형태 변환 필요
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/11834c64-0903-48ff-829c-2516f0daba7c)
#### 📌직렬화 특징
- 프로그램 종료 > 객체 데이터(파일 저장) > 재사용 가능
- 여러 형태 수행 가능
- 클래스 속성 달라지면 사용 불가
- 자바(JVM) > 송신부/수신부 운영체제 달라도 상관 없음
#### 📌 직렬화 조건
- `java.io.Serializable` 인터페이스 상속받은 객체 (기본 조건)
    - `JVM` 알려주는 용도
- `Transient` `Static` 키워드 > 제외 가능
### ⭐ `JSON` 직렬화, 역직렬화
- `Jackson` 사용



```java
List<Member> memberList = new ArrayList<>();
memberList.add(new Member(1001, "Kate", 30));
memberList.add(new Member(1002, "Jason", 23));
memberList.add(new Member(1003, "Aaron", 35));

ObjectMapper mapper = new ObjectMapper();

// object to json
mapper.configure(MapperFeature.PROPAGATE_TRANSIENT_MARKER, true);
mapper.writeValue(new File("test.json"), memberList);
```
---

- `implements Serializable` 로 되어있는 `VO(Value Object)` !! ✔ 
  - 잠깐만 ㅋㅋㅋㅋ`VO`? `DTO` 랑 동일한 개념이지만 __READ ONLY__ 속성을 갖는다

### 직렬화
- 자바 시스템 내부에서 사용되는 `Object` `Data` >> 외부의 자바 시스템에서도 사용할 수 있도록 바이트 형태로 데이터 변환하는 기술!
  -  JVM의 메모리에 상주되어 있는 객체 데이터를 바이트 형태로 변환하는 기술 
- 다차원의 자료 >> 파일 저장 / 네트워크 보내기에 알맞게 __일차원__ --> 원래대로 되돌리는 것 : `직렬화(Serialization)`
- 역직렬화: 직렬화의 반대 (바이트 -> data, object)

### 직렬화의 종류
- 크게 2 종류
  - 직렬화되는 자료가 어떤 종류인지 나타내는 데이터 모델
  - 데이터 모델이 언제 결정되느냐에 

#### 1. `schematic`
- 데이터 모델이 고정
- 나중에 바뀌지 않는다는 걸 알고 있고, 직렬화 포멧을 데이터 모델마다 생성해서 쓸 수 있다.
- 프로토콜 버퍼, Cap's Proto 존재
- __성능__ 을 우선 / __데이터 크기__ 우선 >> 이렇게 나눌 수 있다 >> 어느 쪽이든 `schemaless` 한 직렬화보다는 효율적!

#### 2. `schemaless`
- 대부분의 데이터 모델을 포함하는 __범용 데이터 모델__ 쓰는 접근
- 재귀 ❌ 순서 ⭕ >> 순열 및 순서 ❌ >> 집합 ==> `JSON` `MessagePack` 같은 것들 해당 
- `XML` + DTO / XML Schema >> 스키마 존재하면 >> `schematic` 아니면 `schemaless` [참고자료](https://j.mearie.org/post/122845365013/serialization#notes)

### 자바에서의 직렬화(`Serializable`)
- 자바에서의 직렬화 >> JVM 메모리에서만 상주되어있는 객체 데이터를 그대로 영속화가 필요할 때 사용!
  - 네트워크 전송 가능
  - 필요할 떄 객체 데이터를 가져와서 역직렬화하여 객체 바로 사용 가능
#### 서블릿 세션(`Servlet Session`)
- 서블릿 기반의 WAS(톰캣, 웹로직 등) 대부분 세션의 자바 직렬화 지원
- 파일로 저장하거나 세션 클러스터링, db에 저장하는 옵션 등을 선택하게 된다면 세션 자체가 직렬화 되어 저장되어 전달
#### 캐시(`Cache`)
- 캐시 할 부분을 자바 직렬화된 데이터 저장해서 사용!
#### `RMI` (Remote Method Invocation)
- 원격 시스템간의 메시지 교환을 위해 사용하는 자바에서 지원하는 기술
- 원격 시스템의 메소드를 호출 시에 전달하는 메시지(객체)를 자동으로 직렬화 시켜 사용

### 자바의 `Serializable` ✔
- `java.io.Serializable` 인터페이스 보면 구현해야 할 메서드 없다.
- 그 이유는 Serializable 인터페이스 구현한 구현체 >> __직렬화 대상__ 이라는 것을 `JVM`에게 알려주는 역할만 수행!
- 떄문에 불필요한 직렬화는 오버헤드의 원인 ㅠ,ㅠ 
- 하지만!! `Serializable` 은 직렬화 작업을 하는 것이 아니라 단지 해당 클래스의 인스턴스는 직렬화할 수 있다는 것을 선언하는 것!! 문제 되지 않는다.
  - 👌 참고로 자바의 `ArrayList` `HashMap` 등 기본 컬렉션 구현체 모두 ✔ `Serializable` 구현하고 있는 것 비슷


[참고자료](https://haranglog.tistory.com/4)
