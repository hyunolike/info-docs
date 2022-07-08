## Protocol Buffer - feat. `gRPC`
- 구조화된 데이터를 직렬화하는 방식
  - 직렬화: 데이터를 파일로 저장하거나 네트워크 통신에 사용하기 위한 형식, 즉 바이트  스트림 형태로 변환하는 것

### 1. 사용 비교
#### `JSON`
```javascript
let person = { name: "jinny", age: 27};

let serializedJson = JSON.stringify(person); // 데이터 크기 25byte
```

#### `Protocol Buffer`
```java
message Person{
  string name = 1; 
  int32 age = 2;
} 
// 데이터 크기 9byte
```
- `ProtoFile` 필요✔ >> 프로토콜 버퍼 방식을 사용하기위해 필요한 파일

### 2. 장단점
- 장점
  - 직렬화, 역직렬화 속도 빠름
  - 직렬화된 파일의 크기 월등히 감소
  - 대용량 데이터 처리할 때 성능 좋음 
  - 스키마 존재 >> 쉽게 직렬화, 역직렬화 가능 >> 내부 서비스 사용시 효과적 ✔
- 단점
  - JSON과 달리 사람이 읽기 어려움
  - proto 파일 없으면 데이터 해석 불가
