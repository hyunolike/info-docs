## 클로져
> [참고자료](https://joshua1988.github.io/vue-camp/js/closure.html)
- 사전 개념: 스코프 `Scope` >> 식별자 접근 규첵에 따른 유효 범위
- ✔ 함수의 실행이 끝난 후에도 함수에 선언된 변수의 값을 접근할 수있는 자바스크립트의 성질 >> 다른 언어와의 유일한 특징!
- 클로져 개념 자체 >> 자바스크립트의 고유 개념 아님! - [참고자료](https://hanamon.kr/javascript-%ED%81%B4%EB%A1%9C%EC%A0%80/)
  - 여러 함수형 프로그래밍 언어에서의 공통적으로 발견되는 특성! 
- ⭐자신이 선언될 당시의 환경을 기억하는 함수 >> 이렇게 기억!!
- 클로저는 내부함수가 상위 스코프의 식별자를 참조! >> 그 상위 스코프 바깥에서 사용했을 때 그 상위 스코프의 식별자 수정할 수 없는 형태

### 클로져 만드는 2가지 형태
```javascript
// 클로저를 만드는 형태 1. - 중첩함수
function outerFn() {
  let x = 10;
  return function innerFn(y) { // innerFn 함수는 클로저다.
    return x = x + y;
  }
}
let a = outerFn(); // 외부함수 호출은 한번만. 이제 a 변수는 innerFn 함수를 참조한다.
a(5); // 15;
a(5); // 20;
a(5); // 25;

// 클로저를 만드는 형태 2. - 전역에 선언한 변수를 박스 안에서 함수로 정의하고 전역에서 호출
let globalFunc;
{
  let x = 10;
  globalFunc = function(y) { // globalFunc 함수는 클로저다.
    return x = x + y;
  }
}
globalFunc(5); // 15;
globalFunc(5); // 20;
globalFunc(5); // 25;
```
