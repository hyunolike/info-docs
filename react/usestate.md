## useState 초기값 설정
> [참고자료](https://muscardinus.tistory.com/entry/useState-%EC%B4%88%EA%B8%B0%EA%B0%92)


```js
const [state, setState] = useState(초기값);

const [state, setState] = useState(complicatedFunction()); ⭐ 매호출마다 복잡한 연산 ㅠ,ㅠ
``` 

### 초기값 ✔
- 😛 첫 렌더링때만 실행!!


```js
const [state, setState] = useState(() => complicatedFunction());
```
