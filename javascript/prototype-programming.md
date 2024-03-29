## 프로토타입 기반 프로그래밍
> [참고자료](https://ko.wikipedia.org/wiki/%ED%94%84%EB%A1%9C%ED%86%A0%ED%83%80%EC%9E%85_%EA%B8%B0%EB%B0%98_%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D) <br>
> [참고자료 - 블로그](https://evan-moon.github.io/2019/10/23/js-prototype/)
- ⭐자바스크립트 >> 프로토타입 기반 프로그래밍
- ✔ `ES6` 부터 **클래스** 대부분 사용! 익숙한 개념이 아님 ㅠ.,ㅠ `문법설탕`
  - 프로토타입으로 클래스 흉내낸거!

### 1. 프로토타입 = 디자인 패턴
- **프로토타입 패턴**: 객체 효율적으로 생성하는 방법을 다루는 패턴 중 하나 ✔
  - 객체 생성하는 비용 클 때, 이를 회피하기 위해 사용
- ⭐즉, 원본 객체 존재하고 그 객체를 복제해서 새로운 객체를 생성하는 방법

### 2. 자바스크립트의 프로토타입 
> 자바스크립트 함수 생성할 때마다 자동으로 그 함수의 프로토타입 객체도 함께 생성하고 `prototype` 프로퍼티에 연결!
- 🖐자바는 클래스 기반 프로그래밍!
- 자바스크립트 >> 모든 **객체 생성** >> 프로토타입 사용

#### 2-1. 객체 생성 방법
- 객체: 현실의 사물을 프로그램에 반영
- **함수** 를 통해 객체 생성! ✔
- ![image](https://user-images.githubusercontent.com/61215550/201567986-038f3f3d-a1e6-4f61-96b8-da2282bccb5d.png)
- 생성된 객체가 자신의 원본 객체에 접근할 수있는 프로퍼티 `__proto__`
  - 🖐현재는 `Object.getPrototypeOf()`
#### 2-2. 요약
1. 프로토타입 패턴 >> 객체 생성할 때 원본 객체를 복제하여 생성하는 방법
2. 자바스크립트 >> 객체 생성할 떄 **프로토타입 패턴** 사용
3. 자바스크립트 >> 객체 생성할 때 **함수** 사용
- ![image](https://user-images.githubusercontent.com/61215550/201568278-f9979d0a-4a0d-4e3e-af92-d32fdb2801e6.png)

### 3. 프로토타입 체인
- 자바스크립트 내의 사용되는 모든 객체 >> 프로토타입 기반 방식 정의하고 생성
- ⭐`Object` 함수의 프로토타입인 `Object.prototype` 을 시작으로 해서 복제
- ![image](https://user-images.githubusercontent.com/61215550/201568538-307f183c-74c7-402c-b640-66ca4a3e48b2.png)
