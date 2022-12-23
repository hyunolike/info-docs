## `this` 개념 & 바인딩 `업데이트 2022/12/23`
- ✔ this의 주요 목적
  - 작성된 코드를 여러 목적으로 재사용하기 위함!
- 함수 다양 >> 함수별로 this 다르게 해석

> [참고자료](https://oneroomtable.tistory.com/entry/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-this%EB%9E%80-%EB%8C%80%EC%B2%B4-%EB%AC%B4%EC%97%87%EC%9D%BC%EA%B9%8C)
- `this` 고정된 값에 바인딩되지 않음
- 함수가 호출되는 방식에 따라 `동적` 으로 결정 ⭐

### 1. this의 이해
- 바인딩: `this`의 호출 방식에 따라 특정 **객체** 에 연결
- `this` 바인딩 3가지 
  - 일반 함수 내부 >> 전역 객체 바인딩
  - 메서드 내부 >> 메서드를 호출한 객체 바인딩
  - 생성자 함수 내부 >> 생성자 함수가 생성할 **인스턴스(객체)** 바인딩 ✔
  - `Call` `Apply` `Bind` 통한 호출 방식으로 나뉨

### 2. 정리
> `this` 함수 호출 방식에 따라 **동적** 으로 결정!! 


|일반 함수 호출|메서드 호출|인스턴스 호출|
|---------|--------------|----|
|![image](https://user-images.githubusercontent.com/61215550/199139893-1a8ee005-3bdb-4d89-9148-f25d30a3a71c.png)|![image](https://user-images.githubusercontent.com/61215550/199139908-6975d5e3-51a2-424d-b9d2-fdb80061fe74.png)|![image](https://user-images.githubusercontent.com/61215550/199139944-ad6612dd-c7da-45b4-b96c-15c94cd6806a.png)
|


## (추가) `call` `apply` `bind` 설명
> [참고자료](https://oneroomtable.tistory.com/entry/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-call-apply-bind-%EC%84%A4%EB%AA%85)
