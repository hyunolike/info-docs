## 옵셔널 체이닝 `?.` 중첩객체 에러 없이 안전하게 접근
> [참고자료](https://ko.javascript.info/optional-chaining)
### 사용안한 경우 발생하는 에러 😂
```javascript
let user = {}; // 주소 정보가 없는 사용자

alert(user.address.street); // TypeError: Cannot read property 'street' of undefined
```


- 기존 `&&` 사용
### 1. 옵셔널 체이닝
- `?.`: `undefined` `null` 이면 평가 멈추고 `undefined` 반환
- 옵셔널 체이닝 남용 금지
  - 꼭 필요한 대상에만 사용!
- `?.` 앞에는 변수 선언 필요
- delete 연산자 > `delete user?.name` //유저.이름 존재하면 삭제처리
