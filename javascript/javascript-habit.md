## 자바스크립트에서 지양해야 할 습관들
> 🥳 코드를 작성하는 것보다 읽는데 많으 시간을 소비해!!
### 1. let, const 대신 `var` 사용하는거 
- let, const 사용해야 하는 이유
    - 범위가 명획해짐
    - 전역 객체 생성하지 않음
    - 동일 변수명을 다시 선언할 때 오류 표시
### 2. 주석 사용해 코드 설명하는 것
- 주석은 소프트웨어 작성 시, 기본적인 부분
    - ✅ 더 중요한 것 >> 코드를 읽기 편하게 작성하는 것 !!! 맥락 설명

### 3. === 대신 `==` 사용하는 것 
- `===` 완전 항등 연산자


```js
[] == 0
> true
```

### 4. 옵셔널 체이닝 사용하지 않는 것
- 옵셔널 체이닝 연산자 `?.`
- 이걸 사용하면 자바스크립트는 에러를 생성하지 않지만, 해당 프로퍼티가 정의되지 않았음을 알려줌 > 오류에 대해 미리 예방하는 것!

### 5. 매직 넘버와 매직 스트링을 사용하지 않는 것
- 매직 넘버 / 매직 스트링 >> 코드에 직접 사용되는 숫자 또는 문자열
- 상수에 이러한 값 할당하는 것 좋아

### 6. API 호출 오류에 대한 부적절한 처리
- 언제나 `async/await` 안에서 `try/catch` 사용해 에러 처리!!

### 7. 객체를 단일 매개변수로 사용하는 것

### 8. 약어 사용하지 않는 것
```js
if(x !== "" && x !== null && x !== undefined){...}

😛 위에꺼랑 같은거
if( !!x ) {...}
```