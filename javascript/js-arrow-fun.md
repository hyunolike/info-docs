## 화살표 함수 주의사항
> [참고자료](https://inpa.tistory.com/entry/JS-%F0%9F%93%9A-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%ED%99%94%EC%82%B4%ED%91%9C-%ED%95%A8%EC%88%98-%EC%A0%95%EB%A6%AC#%EB%A7%A4%EA%B0%9C%EB%B3%80%EC%88%98_%ED%91%9C%ED%98%84)
- ⭐ 자신만의 `this` 가지지 않는다

#### 1. 일반 객체의 메소드 사용 ❌
```js
const person = {
  name: 'Lee',
  sayHi: () => console.log(`Hi ${this.name}`)
};

person.sayHi(); // Hi undefined
```


- `this` 가 없기에 메소드를 호추한 객체를 가리키지 않고 상위 컨택스트인 전역 객체 `window` 가리킨다
#### 2. `prototype` 메소드 사용 ❌
```js
javascript// 모든 객체는 기본적으로 Object객체에 프로토타입 체이닝 되어있다.
const person = { 
  name: 'Lee',
};

Object.prototype.sayHi = () => console.log(`Hi ${this.name}`);

person.sayHi(); // Hi undefined
```
#### 3. 생성자 함수로 사용 ❌
```js
const Foo = (name) => {
	this.name = name
};

// 화살표 함수는 prototype 프로퍼티가 없다
console.log(Foo.hasOwnProperty('prototype')); // false

const foo = new Foo("FFF"); // TypeError: Foo is not a constructor
```
#### 4. ⭐`addEventListner` 콜백 함수 조심!! 
- 현업에서는 `event` 객체의 `currentTarget` / `target` 프로퍼티 사용해서 이벤트가 발생한 요소에 접근하는 편


```js
<button>Click me!</button>

<script>
let button = document.querySelector('button');

button.addEventListener('click', (event) => {
  console.log(event.target); // <button> 요소
});
</script>
```


##### 4-1. 일반 메소드
```js
<button>Click me!</button>

<script>
let button = document.querySelector('button');

button.addEventListener('click', function() {
  console.log(this); // <button> 요소
});
</script>
```
##### 4-2. 화살표 메소드
```js
<button>Click me!</button>

<script>
let button = document.querySelector('button');

button.addEventListener('click', () => {
  console.log(this); // window 객체
});
</script>
```
