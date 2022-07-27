## Redux
> [참고자료](https://kyun2da.dev/%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AC/Redux-%EC%A0%95%EB%A6%AC/)
- 상태 관리 라이브러리

### 1. 용어
#### 1.1 액션 `Action`
- 상태 변화 필요 >> 액션 일으켜야됨!!
- 액션은 `객체` 

```javascript
{
   type: 'ADD_TODO',
   data: {
       id: 1,
       text: '리덕스 배우기'
   }
}
```

#### 1.2 액션 생성함수 `Action Creator`
- 액션 객체 만들어주는 함수


```javascript
function addTodo(data) {
 return {
   type: 'ADD_TODO',
   data,
 }
}
```
#### 1.3 리듀서 `reducer`
- 변화를 일으키는 것
- 현재상태와 액션객체 받아 필요하다면 >> 상태 리턴하는 함수
- 액션 유형 기반으로 이벤트 처리하는 **이벤트 리스너**


```javascript
const initialState = {
 counter: 1,
}
function reducer(state = initialState, action) {
 switch (action.type) {
   case INCREMENT:
     return {
       counter: state.counter + 1,
     }
   default:
     return state
 }
}
```

#### 1.4 스토어 `Store`
- 상태 들어가 있음 
- 하나의 프로젝트 >> 하나의 스토어

#### 1.5 디스패치 `Dispatch`
- 스토어의 내장 함수 중 하나
- 액션 객체를 넘겨줘서 상태를 업데이트 하는 유일한 방법
- 이벤트 트리거

#### 1.6 구독 `Subscribe`
- 리스너 함수 >> 파라미터 넣어 호출하면 상태 업데이트될 때마다 호출
- 일종의 이벤트 리스너

```javascript
const listener = () => {
 console.log('상태가 업데이트됨')
}
const unsubscribe = store.subsribe(listener)

unsubscribe() // 추후 구독을 비활성화할 때 함수를 호출
```

### 2. 흐름
![](https://kyun2da.dev/c98922b5a476e12b853576324f12f5c4/redux-data-flow.gif)

