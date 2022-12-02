## 생성자 함수
> [참고자료 - 공식문서](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function) <br>
> [참고자료](https://ko.javascript.info/constructor-new)
- `{...}` 객체 리터럴 사용해 객체 쉽게 생성
  - 😂 유사한 객체 여러개 만들 경우는? 복수의 사용자, 메뉴 내 다양한 아이템 ㅠ,ㅠ
  - ✔ `new` 연산자와 생성자 함수를 사용해 유사한 객체 여러 개 쉽게 만들어 버렷
### 1. 생성자 함수란?
> 생성자 함수와 일반 함수 기술적 차이 없어!! 
- 함수 이름의 첫 글자 대문자
- 반드시 `new` 연산자 붙여 실행
#### 1-1. 동작 방식
1. 빈 객체를 만들어 `this` 할당
2. 함수 본문 실행 
3. `this` 반환
- ![image](https://user-images.githubusercontent.com/61215550/205191993-ea2d1c72-a6fc-4c9a-bba9-496725a5ea5e.png)

### (팁) `new function() {...}`
- 재사용 필요 없는 복잡한 객체 만들 때는? >> **익명 생성자 함수** ✔
