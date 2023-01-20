## 화살표 함수 vs 일반함수 `with this`
> [참고자료](https://velog.io/@yjh8806/%ED%99%94%EC%82%B4%ED%91%9C-%ED%95%A8%EC%88%98%EC%99%80-%EC%9D%BC%EB%B0%98-%ED%95%A8%EC%88%98%EC%9D%98-%EC%B0%A8%EC%9D%B4)
- ✔ 바인딩: 함수 호출, 실제 함수 연결하는 방법
  - 함수를 호출하는 부분! >> 실제 함수 위치한 메모리 연결하는 것 === **바인딩**

### 😛 `this`
#### 1. 일반함수
- 자바스크립트의 모든 함수 >> 실행 시 >> 함수 내부 `this` 객체 추가
- 함수 선언시 정적으로 결정 x >> 함수 어떻게 호출 >> this 바인딩할 객체 **동적으로 결정** ✔
#### 2. 화살표 함수
- 선언 시 `this` 바인딩할 객체 **정적으로 결정** ✔
- 화살표 함수 언제나 상위 스코프의 this 가리킴!