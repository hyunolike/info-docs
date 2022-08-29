## useReducer에서 `typescript` 적용 방법
> [참고자료](https://coding-w00se.tistory.com/m/44)
- 컴포넌트 외부에서 상태 관리하기 위한 방법 >> `useReducer`
- `useState` `useReducer` 모두 존재 >> 프로젝트 큰 경우 `useReducer` 사용하자

### ⭐1. reducer의 type 지정
```typescript
function reducer(state: stateType, action: actionType): stateType {}
---

import React, {useReducer} from 'react';

interface Action {
  type: String
}

// state와 action에 모두 타입을 선언
// reducer의 반환 값은 state 이므로 반환 값 타입은 state와 일치하도록 지정
function reducer (state: number, action: Action): number {  
    switch(action.type) {
        case "INCREMENT":
            return state+1;
        case "DECREMENT":
            return state-1;   
        default:
            return state;
    }
}

function Counter(props: CounterProps) {
    const [ number, dispatch ] = useReducer(reducer, 0);

    const onIncrease: () => void = () => {
        dispatch({ type: "INCREMENT" });
    }

    const onDecrease: () => void = () => {
        dispatch({ type: "DECREMENT" });
    }

    return (
        <>
            <h1>{number}</h1>
            <button onClick={onIncrease}>+1</button>
            <button onClick={onDecrease}>-1</button>
        </>
    );
}

export default Counter;
```

### 2. 실습 예제 적용한 코드
```typescript
import { useReducer, useRef } from 'react';
import './App.css';
import { BrowserRouter, Route, Routes } from 'react-router-dom';

import Home from './pages/Home';
import Edit from './pages/Edit';
import New from './pages/New';
import Diary from './pages/Diary';
import RouteTest from './components/RouteTest';
import MyButton from './components/MyButton';
import MyHeader from './components/MyHeader';


// reducer의 반환값은 state / 반환 값 타입은 state와 일치하도록 지정 ⭐
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

function App() {
  const [data, dispatch] = useReducer(reducer, []);

  const dataId = useRef(0);
  //create
  const onCreate = (date: any, content: any, emotion: any) => {
    dispatch({
      type: 'CREATE',
      data: {
        id: dataId.current,
        date: new Date(date).getTime(),
        content,
        emotion,
      },
    });
    dataId.current += 1;
  };

  //remove
  const onRemove = (targetId: any) => {
    dispatch({ type: 'REMOVE', targetId });
  };
  //edit
  const onEdit = (targetId: any, date: any, content: any, emotion: any) => {
    dispatch({
      type: 'EDIT',
      data: {
        id: targetId,
        date: new Date(date).getTime(),
        content,
        emotion,
      },
    });
  };

  const env = process.env;
  env.PUBLIC_URL = env.PUBLIC_URL || '';

  return (
    <BrowserRouter>
      <div className="App">
        <MyHeader
          headText={'App'}
          leftChild={
            <MyButton text={'왼쪽 버튼'} onClick={() => alert('왼쪽 버튼~')} />
          }
          rightChild={
            <MyButton
              text={'오른쪽 버튼'}
              onClick={() => alert('오른쪽 버튼~')}
            />
          }
        />
        <h2>App.js</h2>

        <MyButton
          text={'버튼'}
          onClick={() => alert('버튼 클릭해')}
          type={'positive'}
        />

        <MyButton
          text={'버튼'}
          onClick={() => alert('버튼 클릭해')}
          type={'negative'}
        />

        <MyButton
          text={'버튼'}
          onClick={() => alert('버튼 클릭해')}
          type={'default'}
        />
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/edit" element={<Edit />} />
          <Route path="/new" element={<New />} />
          <Route path="/diary" element={<Diary />} />
          <Route path="/diary/:id" element={<Diary />} />
        </Routes>
        <RouteTest />
      </div>
    </BrowserRouter>
  );
}

export default App;

```
