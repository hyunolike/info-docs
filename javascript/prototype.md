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
