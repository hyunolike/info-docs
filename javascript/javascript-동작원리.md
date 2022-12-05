## JavaScript 동작 원리
> [참고자료](https://joshua1988.github.io/web-development/translation/javascript/how-js-works-inside-engine/)

### 1. 자바스크립트 엔진
- ![image](https://user-images.githubusercontent.com/61215550/205553742-bf90cece-1e65-4730-b4ce-06fa63bafa28.png)
- ✔ `Call Stack` 호출 스택 >> 기본 작업 `싱글스레드`
  - 코드 실행에 따라 호출 스택이 쌓이는 곳
- ✔ `Memory Heap`
  - 메모리 할당이 일어나는 곳

### 2. 자바스크립트 런타임 
> 특정 언어로 만든 프로그램들을 실행할 수 있는 환경
- ![image](https://user-images.githubusercontent.com/61215550/205554155-6def277b-cfa9-4629-bd05-5d011ca523fa.png)
- 엔진 밖에서 관여하는 요소
  - `Web API`: 브라우저에서 제공! 메소드 지원
  - `Task Queue`: 이벤트 발생 후 호출되어야 할 콜백 함수들이 기다리는 공간 / 정해진 순서대로 줄 `Callback Queue`
  - `Event Loop`: 이벤트 발생 시 호출할 콜백 함수들을 관리, 호출된 콜백 함수의 실행 순서 결정
#### 2-1. 자바스크립트에서 비동기 처리 필요한 이유
- 서버로 데이터 요청 시, 언제 그 요청에 대한 응답 할지도 모르는 상태 >> 다른 코드 실행 안하고 기다릴 수는 없기에..ㅋㅋㅋㅋ(당욘)

### 3. 콜백함수 & 프로미스 & Async Await
- ...


