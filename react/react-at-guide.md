## 리엑트 설계 가이드
> [참고자료](https://www.stevy.dev/react-design-guide/)
- 크게 2가지
  - 👨‍🌾 `프로젝트 구조 설계 패턴`
  - 👨‍🌾 `컴포넌트 설계 패턴`

### 1. 리엑트 좋은 설계 고민해야하는 이유 (리엑트 설계하는 원칙)
- `확장성` `재사용` 있는 코드 만들어야해
- `관심사`에 따라 코드 `분리`하고 `단일 책임` 을 가지는 컴포넌트 만들어야 해
- 외부에 `제어를 위임` 시키는 것을 고려해야해

### 2. 👨‍🌾 프로젝트 구조 설계 패턴
#### 2.1. 파일의 기능 / 라우터에 따라서 분류
```
// 기능이나 경로로 폴더 나누기 / 필요한 js/ css/ test 코드 모으기
common /
    Avatar.js;
    Avatar.css;
    APIUtils.js;
    APIUtils.test.js;
feed /
    index.js;
    Feed.js;
    Feed.css;
    FeedStory.js;
    FeedStory.test.js;
    FeedAPI.js;
profile /
    index.js;
    Profile.js;
    ProfileHeader.js;
    ProfileHeader.css;
    ProfileAPI.js;
```
#### 2.2. 파일 유형에 따라 분리
```
// 더 나아가면 아토믹 디자인
// 아토믹 디자인: 페이지를 나눌 수 없을때까지 쪼개서 재사용 극대화 
api /
    APIUtils.js;
    APIUtils.test.js;
    ProfileAPI.js;
    UserAPI.js;
components /
    Avatar.js;
    Avatar.css;
    Feed.js;
    Feed.css;
    FeedStory.js;
    FeedStory.test.js;
    Profile.js;
    ProfileHeader.js;
    ProfileHeader.css;
```
#### 2.3. 여러가지에 의해서 분리한 예
```
// 도메인 의존성, 기능, 재사용성, 비즈니스 로직 모두 고려해서 나눈 예
-src /
  ---domain / // 특정 도메인에 의존적인 컴포넌트
  -----User /
  -------Profile /
  -------Avatar /
  -----Message /
  -------MessageItem /
  -------MessageList /
  -----Payment /
  -------PaymentForm /
  -------PaymentWizard /
  -------services /
  ---------Currency /
  -----------index.js;
-----------test.js;
-----Error /
  -------ErrorMessage /
  -------ErrorBoundary /
  -------utils / // Error에서만 쓰이는 유틸은 따로 둘 수도 있다
  ---------ErrorTracking /
  -----------index.js;
-----------test.js;
---components / // 재사용이 가능한 컴포넌트들
  -----App /
  -----List /
  -----Input /
  -----Button /
  -----Checkbox /
  ---hooks /
  ---context /
  ---utils /
  -----Format /
  -------Date /
  ---------index.js;
---------test.js;
// 관심사에 따른 역할에 따라 나눈 예
|── src
│   ├── application // 상태관리, 유틸, 상수
│   │   ├── common
│   │   ├── filters
│   │   ├── logger
│   │   ├── models
│   │   ├── persist
│   │   ├── plugins
│   │   ├── store
│   ├── infrastructure // axios, api handeler, 공통 컴포넌트
│   │   ├── api(services)
│   │   ├── components (common components)
│   ├── presentation // 비즈니스 로직 컴포넌트
│   │   ├── container
│   │   ├── component
├── index.js
```
### 3. 👨‍🌾 컴포넌트 설계 패턴
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/84cdd7c0-b9ae-47fd-bd40-5fc71b61475e)
#### 3.1. 합성 컴포넌트 패턴
- `Prop Drilling` 문제 해결책
- 컴포넌트 커스터마이징 & 가독성 좋은 api
#### 3.2. 제어 Props 패턴
- 제어컴포넌트로 컴포넌트 변환 하는 패턴
- `single source of truth`인 외부 state에 유저 > `custom logic` 넣을 수 있게함
#### 3.3. Custom Hook 패턴
- 제어 역전 측면에서 커스텀 훅스를 이용하면 외부로 로직을 위임할 수 있음
#### 3.4. Props Getter 패턴
- ...
#### 3.5. State Reduce 패턴
- 제어역전 심화된 패턴
- 사용자에게 컴포넌트 동작 > 어떻게 변화 > 가장 진보된 방법
- 커스텀 훅과 비슷 > 사용자는 reducer에 정의 다할 수 있음
