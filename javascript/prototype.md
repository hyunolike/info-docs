## Prototype 진짜 이해할래
- 프로토타입 == 원형(원래의 형태) ✔ >> 상속이란 개념 제공!
- 생성자는 함수 >> 함수 호출 할때 `new` >> 생성자 >> 새로운 객체 만들어서 리턴 ⭐
  - 객체 리터럴 `{ ... }` >> 이건 비어있는 객체야
- ![image](https://user-images.githubusercontent.com/61215550/205194091-a0b11c15-1fd0-43ff-bef2-c35e4cb192fa.png)
### 😛 prototype chain
- ![image](https://user-images.githubusercontent.com/61215550/205195149-87e086d5-f69a-4129-85ea-a0252ad16829.png)


## Prototype 이해 `추가 2022/12/02`
> [참고자료](https://www.nextree.co.kr/p7323/)
- ⭐ 자바스크립트는 `클래스` 라는 개념이 없어!! >> 기존의 객체 `복사` 해 **새로운 객체 생성**하는 프로토타입 기반의 언어!
- 프로토타입 기반 언어 >> 객체 원형인 프로토타입 이용해 새로운 객체 만들어
- 프로토타입 >> 객체 확장하고 객체 지향적인 프로그래밍 가능하게 해줌
- **2가지**로 해석 😛
  1. 프로토타입 객체를 참조하는 `prototype` 속성
  2. 객체 멤버인 `proto` 속성이 참조하는 숨은 링크

## Prototype 
> [참고자료](https://ko.javascript.info/prototype-inheritance)
- 기존 A의 약간의 기능을 얹어 B, C 객체 만들자
- 자바스크립트 언어의 고유 기능 >> `prototypal inheritance` 이용 ✔

### `[[Prototype]]`
- 자바스크립트 객체 >> 명세서에서 명명한 `[[Prototype]]` 이라는 숨김 프로퍼티 존재

### `__proto__` 와 `[[Prototype]]` 은 다르다! ⭐
- `__proto__`: `[[Prototype]]` 의 getter, setter 
- ![image](https://user-images.githubusercontent.com/61215550/178185992-4b81ad16-dc1c-4cbe-bdd1-36a3dc5cc67c.png)

### 프로토타입은 읽기 전용
- 수정할 때는 직접 객체로 ~

### `this` 가 나타내는 것
- `this` >> 프로토타입에 영향 없다
- ![image](https://user-images.githubusercontent.com/61215550/178186744-dc0132b1-8d9d-41e1-b666-964c35ecec54.png)

### `for-in` 반복문
- 상속 프로퍼티 >> 순회대상 포함!

### ✔ 함수의 prototype 프로퍼티
- 자바스크립트 만들어졌을 당시 >> 프로토타입 기반 상속이 자바스크립의 주요 기능 ⭐
- ![image](https://user-images.githubusercontent.com/61215550/178187300-9914481f-30b3-4e60-a033-6655721c9aa4.png)

### ✔ 내장 객체의 프로토타입
- 모든 내장 생성자 함수 >> `prototype` 프로퍼티 사용!
