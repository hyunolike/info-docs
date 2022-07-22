## Flux patter
> [참고자료](https://medium.com/hcleedev/web-react-flux-%ED%8C%A8%ED%84%B4-88d6caa13b5b)

|기존 문제점 `MVC`|`Flux`|
|-----------------|----------|
|![image](https://user-images.githubusercontent.com/61215550/180374297-6d0948c1-3bf0-4379-94c6-eccdccfadad2.png)|![image](https://user-images.githubusercontent.com/61215550/180374325-74f0e389-cf35-49a9-ac53-22c38e6f01bb.png)|

### Action
- `Action Controller` 
- 클릭 이벤트 발생 시 >> 그 이벤트가 발생했음을 Action정보를 담고 있는 객체 생성 >> `Dispatcher` 전달하는 역할

### Dispatcher
- 들어오는 `Action` 객체 정보 받아 실제로 어떤 행동을 할지 결정
- 중앙 허브 역할
- 주로 `Store` 있는 정보에 접근해 수정하는 명령 다수
  - 상태 관리와 관련된 문제
- `Switch` 문 사용해 Action 객체 나누어 처리

```javascript
function reducer(state, action) {
  switch (action.type) {
    case 'ADD':
      return {
        number: state.number + 1
      }
    default:
      return state;
  }
}
```

### Store
- 데이터, 상태 가지고 있음
- Store --- Dispatcheer 연결 Store에 접근가능하도록 callback 명령 제공 `React`
- 여기서 가진 상태 `View` 접근 / 상태 변경 시 `View` 에서도 이를 반영

### View
- 화면 렌더링
- 
