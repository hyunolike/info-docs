## 버블링과 캡처링 `추가 2022/12/06`
> [참고자료](https://ko.javascript.info/bubbling-and-capturing)
- DOM 이벤트 정의한 이벤트 흐름

### 🦅이벤트 버블링 & 이벤트 캡처 & 이벤트 위임
> [참고자료](https://joshua1988.github.io/web-development/javascript/event-propagation-delegation/)
- 브라우저 어떻게 특정 화면 요소의 이벤트 감지하는지! 그 이벤트를 어떻게 다른 화면 요소에 전파하는지!
#### ⚡이벤트 감지하는 방법 2가지 
##### 1. 이벤트 버블링
> ✔이벤트 발생 시, 상위로 전달하기!
- ![image](https://user-images.githubusercontent.com/61215550/205816340-f253c26a-4435-4dc5-bf14-875ff5d1e2b5.png)
##### 2. 이벤트 캡쳐
> ✔이벤트 발생 시, 발생한 지점 찾아내기!
- ![image](https://user-images.githubusercontent.com/61215550/205816595-913c93df-a971-4e9a-9b8f-4f03e59360f1.png)


|종류|설명|
|----------|--------------|
|캡처링 단계|이벤트가 `하위` 요소로 전파되는 단계|
|타깃 단계|이벤트가 실제 타깃 요소로 전달되는 단계|
|버블링 단계|이벤트가 `상위` 요소로 전파되는 단계|

- ![image](https://user-images.githubusercontent.com/61215550/178401233-01c4d0b3-9895-47fe-85d4-893f30f54a2f.png)

### 1. 버블링
> ⭐꼭 필요한 경우를 제외하곤 버블링 막지 말자!
- 한 요소에 이벤트 발생하면, 이 요소에 할당된 핸들러가 동작하고, 이어서 부모 요소의 핸들러 동작
- 가장 최상단의 조상 요소 만날때까지 이 과정 반복!! >> 요소 각각에 할당된 핸들러 동작

#### 1.1 `event.target`
- 부모 요소의 핸들러 >> 이벤트 정확히 어디서 발생했는지 등에 대한 자세한 정보 얻음
- 이벤트 발생한 가장 안쪽의 요소 >> `타겟(target) 요소` / `event.target` 사용해 접근가능
- `event.target` vs `this(=event.currentTarget)` 
  - `event.target` >> 실제 이벤트 시작된 타깃 요소 / 버블링 진행되어도 변경 x
  - `this` >> 현재 요소 / 현재 실행 중인 핸들러가 할당된 요소 참조

#### 1.2 버블링 중단하기
- `event.stopPropagation()` 사용
  - 위쪽으로 일어나는 버블링 막아줌 / 다른 핸들러들 동작하는 건 막지 못함 ㅠ,ㅠ

### 2. 캡처링
- 하위 요소로 전파
