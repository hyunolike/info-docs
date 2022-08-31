## useReducer
> [참고자료](https://velog.io/@sdc337dc/React-useReducer)
### 1. 개념
#### 1.1 useReduce 상태관리
- 상태 업데이트 방법 중 하나
- useState와 다른 방법

#### 1.2 특징
- 컴포넌트의 상태 업데이트 로직을 컴포넌트에서 분리 가능
- 업데이트 로직을 컴포넌트 바깥에 작성 가능
- 다른 파일 작성한 후 불러와서 사용 가능

#### 1.3 차이 
|useState|useReducer|
|---------|---------|
|![image](https://user-images.githubusercontent.com/61215550/187562888-6477f455-7e32-4134-9bc8-12db6aa25b49.png)|![image](https://user-images.githubusercontent.com/61215550/187562895-6da29f65-b747-4b60-8dd5-003004d3e350.png)|


#### 1.4 실습 코드 참고
- ![image](https://user-images.githubusercontent.com/61215550/187563662-4094d3eb-57cc-46a9-b672-c3546b00d570.png)

### 2. 작성 방법
#### 2.1 필요 4가지
- useReducer 함수
- 상태 state
- 해당 이벤트에 맞는 dispatch 설정 / 이벤트와 dispatch 연결
- 컴포넌트 외부에서 state 업데이트할 reducer 로직 작성

#### 2.2 useReducer()
- `const [상태, 액션을 발생시킬 함수] = useReducer(reducer 함수 ,초기 상태);`
- `const [data, dispatch] = useReducer(reducer, []);`

#### 2.3 상태
- state랑 같음!

#### 2.4 이벤트에 적용되는 dispatch 설정
- `dispatch({type: '구분되는 값'});`
- `dispatch({ type: 'REMOVE', targetId });`

#### 2.5 이벤트 함수 연결
- ![image](https://user-images.githubusercontent.com/61215550/187564258-22a4349a-6ce6-4b31-b647-5f82f9f9cbbb.png)

#### 2.6 state 업데이트할 reducer 로직 작성
```javascript
function reducer(state, action) {
  switch(action.type){
    case '구분값':
      return state 변경
  }
}

const reducer = (state: any, action: any): any => {
  let newState: any = [];
  switch (action.type) {
    case 'INIT': {
      return action.data;
    }
    case 'CREATE': {
      // const newItem = {
      //   ...action.data,
      // };
      newState = [action.data, ...state];
      break;
    }
    case 'REMOVE': {
      newState = state.filter((it: any) => it.id !== action.targetId);
      break;
    }
    case 'EDIT': {
      newState = state.map((it: any) =>
        it.id === action.data.id ? { ...action.data } : it
      );
      break;
    }
    default:
      return state;
  }
  return newState;
};

```

### 3. 정리
- ![image](https://user-images.githubusercontent.com/61215550/187564381-458d1e62-1b87-408d-a418-9d0b04a3d3ee.png)
