## `Promise` `추가 2022/12/05` 
> [참고자료](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- 사전 지식: 자바스크립트 비동기 & 콜백 함수 
#### ⭐자바스크립트의 비동기 패턴! - [참고자료](https://joshua1988.github.io/web-development/javascript/promise-for-beginners/)
- ![image](https://user-images.githubusercontent.com/61215550/205549074-6610d6a4-4fe1-4fda-bddd-493f015b1dfb.png)
- 자바스크립트 비동기 처리에 사용되는 객체
- 😛 객체로써 언젠가 완료될 일(계산)
### 1. `Promise` 필요한 이유
- 주로 서버에서 받아온 데이터를 화면에 표시할 때 사용!
### 2. 프로미스 3가지 상태
- ![image](https://user-images.githubusercontent.com/61215550/205549778-d15b4f2b-81e0-4227-a1ec-2b015dfd628e.png)
#### 2-1. Pending (대기)
```javascript
new Promise();

new Promise(function(resolve, reject) {
  // ...
});
```


- 메서드 호출 시 >> 대기 상태
#### 2-2. Fulfilled (이행)
- `resolve` 같이 실행 >> 이행 상태


```javascript
function getData() {
  return new Promise(function(resolve, reject) {
    var data = 100;
    resolve(data);
  });
}

// resolve()의 결과 값 data를 resolvedData로 받음
getData().then(function(resolvedData) {
  console.log(resolvedData); // 100
});
```
#### 2-3. Rejected (실패)
```javascript
function getData() {
  return new Promise(function(resolve, reject) {
    reject(new Error("Request is failed"));
  });
}

// reject()의 결과 값 Error를 err에 받음
getData().then().catch(function(err) {
  console.log(err); // Error: Request is failed
});
```
### 3. 예외처리는 가급적 `catch()` 사용! ⭐
```javascript
// catch()로 오류를 감지하는 코드
function getData() {
  return new Promise(function(resolve, reject) {
    resolve('hi');
  });
}

getData().then(function(result) {
  console.log(result); // hi
  throw new Error("Error in then()");
}).catch(function(err) {
  console.log('then error : ', err); // then error :  Error: Error in then()
});
```


---
- 프로미스가 생성된 시점에는 알려지지 않았을 수도 있는 값을 위한 **대리자**
- ✔ 미래의 어떤 시점에 결과를 제공하겠다는 약속(프로미스) 반환
- 프로미스 상태 📌
  - 대기 `pending`: 이행하지도, 거부하지도 않은 초기 상태 `비동기 처리 로직이 아직 완료되지 않은 상태`
  - 이행 `fulfilled`: 연산이 성공적으로 완료 `비동기 처리가 완료되어 프로미스가 결과 값을 반환해준 상태`
  - 거부 `rejected`: 연산에 실패 `비동기 처리가 실패하거나 오류가 발생한 상태`
- ![image](https://user-images.githubusercontent.com/61215550/205526433-49175b98-76c3-40c7-9e59-658e12bb6051.png)
