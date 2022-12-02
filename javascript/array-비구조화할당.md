## 비구조화 할당(`구조분해할당`) - `추가 2022/12/02`
> [참고자료](https://learnjs.vlpt.us/basics/06-object.html#%EA%B0%9D%EC%B2%B4-%EB%B9%84%EA%B5%AC%EC%A1%B0%ED%99%94-%ED%95%A0%EB%8B%B9) <br>
> [구조분해할당 참고자료](https://ko.javascript.info/destructuring-assignment)
### (추가) 구조 분해 할당
- `객체` `배열` ⭐자바스크립트에서 가장 많이 사용하는 **자료구조**
  - 개발하다보면 함수에 객체나 배열을 전달하는 경우 >> 데이터 전체가 아닌 **일부!!**  >> 구조분해할당 사용 이유😛
##### 🚩 분해는 파괴를 의미하지 않아
- 어떤 것을 `복사` 한 이후에 변수로 분해 해준다는 의미! >> 구조분해할당
  - 이 과정에서 분해 대상은 수정 또는 파괴되지 않아!!
- (핵심) 배열의 요소 직접 변수에 할당하는 것보다  **코드 양이 줄어든다는 점만 달라져요!** ⚡


```javascript
// let [firstName, surname] = arr;
let firstName = arr[0];
let surname = arr[1];
```
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
