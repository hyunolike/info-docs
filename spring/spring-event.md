## Spring Event
> [참고자료](https://gudwnsgur.tistory.com/19)

### Event
- Spring의 bean 과 bean 사이이 데이터를 전달하는 방법 중 하나
- ✔ publisher와 이를 구독하는 Observer 사이의 결합도 낮추면서 이벤트를 전달하고자 할 때 사용
### 구성 요소 3가지
- `Event Model`: 이벤트 처리하기 위한 필요 데이터 가지고 있음
- `Event Publisher`: 이벤트 발생
- `Event Listener`: 이벤트 받아들이는 거

---
- ![image](https://user-images.githubusercontent.com/61215550/223590314-382b0e02-c708-48da-9a0c-e0cbbcaae12c.png)
- [참고자료](https://wildeveloperetrain.tistory.com/217)
### 사용 이유 ✔
- 서비스 간의 강한 의존성을 줄이기 위함(위 이미지 참고!)
