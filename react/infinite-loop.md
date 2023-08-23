## React에서 무한 루프 일으키는 3가지 방법
> [참고자료](https://alexsidorenko.com/blog/react-infinite-loop/)

### 1. Render 내부 상태 업데이트
> ⭐상태 업데이트 > 재렌더링 트리거 > 상태 업데이트 > 재렌더링 트리거 ...
```js
🖐 문제 발생
function App() {
  const [count, setCount] = useState(0);

  setCount(1); // infinite loop

  return ...
}

😛 문제 해결 - 마운트 1번 상태일때만 업데이트
function App() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    setCount(1);
  }, [])
  

  return ...
}
```
### 2. useEffect 무한 루프 ㅠ,ㅠ
> ⭐count업데이트 → useEffect업데이트된 종속성 감지 → count업데이트 → useEffect업데이트된 종속성 감지 → …
```js
🖐 문제 발생
function App() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    setCount(count + 1) // infinite loop
  }, [count])

  return ...
}

😛 문제 해결 - 기능 업데이트 
function App() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    setCount(previousCount => previousCount + 1)
  }, [])

  return ...
}
```
### 3. 잘못 설정된 이벤트 핸들러 (중요) 👩‍👩‍👧‍👧
> ⭐상태 업데이트 → 재렌더링 트리거 → 상태 업데이트 → 재렌더링 트리거 → …
```js
🖐 문제 발생
export default function App() {
  const [count, setCount] = useState(0);

  return (
    <button onClick={setCount(1)}>Submit</button> // infinite loop
  );
}

😛 문제 해결 - 버튼 클릭한 후에만 업데이트 진행 !
export default function App() {
  const [count, setCount] = useState(0);

  return (
    <button onClick={() => setCount(1)}>Submit</button> // infinite loop
  );
}
```
