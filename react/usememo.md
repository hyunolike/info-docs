## useMemo
> [참고자료](https://www.daleseo.com/react-hooks-use-memo/)

### 1. Memoization
- 기존에 수행한 연산의 결과값을 어딘가에 저장해두고 동일한 입력이 들어오면 재활용하는 프로그래밍 기법
- 중복 연산을 피할수 있기에 메모리 조금 더 쓰더라도 애플리케이션 성능 최적화!

### 2. 랜더링마다 호출되는 컴포넌트 함수
- 함수형 컴포넌트에 `memoization` 적용


```javascript
function MyComponent({ x, y }) {
  const z = compute(x, y);
  return <div>{z}</div>;
}

⭐useMemo 적용!
function MyComponent({ x, y }) {
  const z = useMemo(() => compute(x, y), [x, y]); // useMemo(() => [결과값 생성 함수], [재활용 여부의 기준이되는 입력값 배열])
  return <div>{z}</div>;
}
```

### 3. ...
- 실제 사용할일 별로 없다.
