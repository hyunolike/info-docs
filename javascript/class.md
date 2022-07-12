## Class
```javascript
class MyClass {
  // 여러 메서드를 정의할 수 있음
  constructor() { ... }
  method1() { ... }
  method2() { ... }
  method3() { ... }
  ...
}
```
- 객체의 기본 상태 설정해주는 생성자 메서드 `constructor()` >> `new`에 의해 자동 호출
### function 순수함수로 클래스 구현
```javascript
function User(name){
    this.name = name;
}

User.prototype.sayHi = function (){
    console.log(this.name);
}

let user = new User("hyunho");
user.sayHi();
```
- 모든 함수의 `prototype`에는 __constructor__ 프로퍼티를 기본으로 갖고 있음 >> 명시적으로 만들 필요 없음

### 클래스 표현식
- 함수처럼 클래스도 다른 표현식 내부에서 정의, 전달, 반환, 할당 가능 
```javascript
function makeClass(phrase){
    return class{
        sayHi(){
            console.log(phrase);
        }
    }
}
let User = makeClass("안녕~~~")
new User().sayHi();
```

### getter / setter
...

### ✔ private, protected 프로퍼티와 메서드
> [참고자료](https://ko.javascript.info/private-protected-properties-methods)
- 객체 지향 프로그래밍에서 중요한거 >> 내부 인터페이스 vs 외부 인터페이스 구분 짓기⭐
- 내부 인터페이스: 동일한 클래스 내의 다른 메서드에선 접근할 수 있지만, 클래스 밖에선 접근할 수 없는 프로퍼티와 메서드 ex. 커피머신 내부 부품
- 외부 인터페이스: 클래스 밖에서도 접근 가능한 프로퍼티와 메서드 ex. 커피머신 외부
- `public`: 어디서든 접근할 수 있으며 외부 인터페이스 구성
- `private`: 클래스 내부에서만 접근 가능 / 내부 인터페이스 구성 `#`
- `protected`: 클래스 자신과 자손 클래스에서만 접근 허용 `_`

### ✔ 믹스인
- 특정 행동을 실행해주는 메서드를 제공하는데 단독으로 쓰이지 않고 다른 클래스에 행동을 더해주는 용도


```javascript
let sayHiMixin = {
    sayHi() {
        console.log(`Hello ${this.name}`)
    },
    sayBye() {
        console.log(`Bye ${this.name}`)
    }
}

class User {
    constructor(name) {
        this.name = name
    }
}

Object.assign(User.prototype, sayHiMixin)
new User("hyunho").sayHi()
```
