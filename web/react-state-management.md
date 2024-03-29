## 리엑트 상태관리
> [참고자료](https://velog.io/@yiseul/%ED%94%84%EB%A1%A0%ED%8A%B8%EC%97%90%EC%84%9C-%EC%83%81%ED%83%9C%EA%B4%80%EB%A6%AC)

### ✔ 상태 - `데이터 무결성`
- 컴포넌트 내부에서 관리
- 어플리케이션의 렌더에 영향을 미치는 자바스크립트 객체
- 즉, 어플리케이션의 화면에 영향을 끼치는 자바스크립트 객체이며 사용자와의 인터렉션을 통해 동적으로 계속해서 변화하는 데이터

### 종류
#### 1. 전역상태 `Global State`
- 프로젝트 전체에 영향을 끼치는 상태
- 유저 기능
- `Prop Drilling` 방식
#### 2. 컴포넌트 간 상태 `Cross Component State`
- 여러가지 컴포넌트에서 관리되는 상태
- 다수의 컴포넌트에서 쓰이고 또 영향을 미치는 상태
- 모달
- `Prop Drilling` 방식
#### 3. 지역상태 `Local State`
- 컴포넌트 안에서만 관리되는 상태
- 다른 컴포넌들과 데이터 공유 x

### 리엑트 상태관리 라이브러리
#### 1. Context API
- 컴포넌트 트리 안에서 전역 상태 공유
- 종속성 주입하기 위한 도구
- ✔ 실질적인 상태관리 >> `useState` `useReducer` 
- ✔ `context` >> 단순히 이미 존재하는 상태를 다른 컴포넌들과 **쉽게 공유** 할 수 있게 해주는 역할


|구분|역할|
|--|--|
|Context|전역 상태 저장하는 곳|
|Provider|전역 상태 제공하는 곳| 
|Consumer|제공받은 전역 상태 받아서 사용하는 곳|
#### 2. Redux
- 자바스크립트 앱을 위한 예측 가능한 상태 컨테이너
- 어플리케이션 전체에 대한 **중앙 저장소 역할**


|구분|역할|
|--|--|
|Store|저장소, 즉 전역상태를 저장하는 곳|
|Action|Reducer에게 보내는 Store에 대한 행동을 정의하는 자바스크립트 객체 <br> 😛주문서의 역할|

#### 3. React Query
- 서버와 클라이언트 간 비동기 작업 쉽게 다룰 수 있게 도와주는 라이브러리
- 서버상태 관리하는 라이브러리

#### 4. SWR
- 데이터 가져오기를 쉽게 할 수 있는 리엑트 훅
- HTTP 캐시 무효화 전략 쉽게 할 수 있게 해줌!
- 캐시로부터 데이터를 반환한 후, fetch 요청(재검증)을 하고, 최종적으로 최신화된 데이터를 가져오는 전략이다.
