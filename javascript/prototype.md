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
