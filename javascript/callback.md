## Callback Function
> [참고자료](https://inpa.tistory.com/entry/JS-%F0%9F%93%9A-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%BD%9C%EB%B0%B1-%ED%95%A8%EC%88%98)
### 1. 콜백 함수란?
- 함수 안에서 실행하는 또 다른 함수
- 하나의 함수를 여러가지 응용 가능!!

### 2. 사용 원칙
#### 2.1 익명 함수 사용
```javascript
let number = [1, 2, 3, 4, 5]; number.forEach(function(x) {    console.log(x * 2);});
```
#### 2.2 함수 이름만 넘기기
#### 2.3 전역변수, 지역변수를 콜백함수의 파라미터로 전달
...
### 3. 콜백 지옥 `Callback Hell`
- 비동기 호출이 자주 일어나는 프로그램의 경우 __콜백 지옥__ 발생 ㅠ,ㅠ
