## 향상된 객체 리터럴
> [참고자료](https://mine-it-record.tistory.com/469)

### 1. 객체 프로퍼티 축약
- 프로퍼티 값으로 변수 사용할 경우 >> 프로퍼티 명 생략 가능


```js
let mine = 'Mine';
let it_record = 'itRecord';

const obj = {mine, it_record};
```
### 2. 객체 프로퍼티 키 계산식 사용
- 객체 리터럴 내부에서도 프로퍼티 키 동적 생성 가능


```js 
let mine = 'Mine';
let it_record = 'itRecord';

const obj = {
  [`$[mine}-${it_record}`]: 'it-record'
};
```
### 3. 메서드 생성 방식 간소화
- `function 키워드 생략 가능`


```js
const obj = {
  fun() {
    ...
  }
}
```
### 4. `__proto__` 프로퍼티에 의한 상속
- `__proto__` 프로퍼티 직접 설정 가능


```js
const chicken = {
  name : 'chicken',
  fn() {
    console.log(this.name);
  }
}

const chick = {
  name : 'Chick',
  __proto__ : chicken
}
```
