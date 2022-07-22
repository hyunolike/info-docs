## 비구조화 할당
> [참고자료](https://learnjs.vlpt.us/basics/06-object.html#%EA%B0%9D%EC%B2%B4-%EB%B9%84%EA%B5%AC%EC%A1%B0%ED%99%94-%ED%95%A0%EB%8B%B9)

### 1. 객체 비구조화 할당(구조분해)
> ⭐객체 구조 분해!!!! <br>
> [참고자료](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
- 배열이나 객체의 속성을 해체 >> 그 값을 개별 변수에 담을 수 있게 하는 Javascript 표현식

```javascript
var o = {p: 42, q: true};
var {p, q} = o;

console.log(p); // 42
console.log(q); // true
```

### 2. 배열 비구조화 할당
```javascript
var foo = ["one", "two", "three"];
var [red, yellow, green] = foo;

var foo = ["one", "two", "three"];

var [red, yellow, green] = foo;
console.log(red); // "one"
console.log(yellow); // "two"
console.log(green); // "three"
```
