## Loop 반복
> [참고자료](https://joshua1988.github.io/vue-camp/js/loop.html#for-in)
- 최적의 성능 튜닝 위해서 고의로 >> for문 ✔
- ⭐보통은 `forEach` `for in` `for of` 3가지 주로 사용!!

### 비교
|분류|`forEach()`|`for in`|`for of`|
|--|--|--|--|
|변수타입|배열|배열, 객체|`ES6` 반복 가능한 속성가진 컬렉션|

### ✔ `for of` `for in`
```shell
// 배열을 각각 순회하는 경우
// for of 반복문의 콘솔
10 20 30 

// for in 반복문의 콘솔
0 1 2
```


- `for in`: 인덱스 접근 / **객체**의 속성 순회
- `for of`: 배열의 값 자체 접근 / **반복 가능한 배열의 요소** 순회
