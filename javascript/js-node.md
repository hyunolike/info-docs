## `JavaScript` `Node`
### `JavaScript`
- 독립적 언어가 아닌 스크립트 언어 >> 특정한 프로그램 안에서만 동작 가능
  - 예. 크롬, 파이어폭스, 사파리, 익스플로러 등 `웹 브라우저` ✔
- 웹 브라우저가 없으면 사용할 수가 없음 
- `client` 개발을 위한 용도로 사용

### `Node`
- 로컬 컴퓨터에서 다양한 용도로 확장하기 위해 만들어진 것
- 파이썬처럼 내 컴퓨터에서 file system 이용 가능, 서버 개발, 크롤링 가능
- 자바스크립트 언어 == 파이썬 언어
- 자바스크립트 런타임 >> nodejs는 웹서버 만들 수 있는 하나의 방법 >> 그 자체가 웹서버 ❌
- 크롬, node js >> 같은 엔진(google의 v8 엔진) 공유 
- 크롬, node js >> 다른 런타임 환경 / 다른 실행 환경을 가짐 ✔
- 장점 ⭐
  1. 비동기 처리 >> 빠른 고성능 서버 구현
  2. 한 가지 언어만으로도 서버-클라이언트 모두 개발 가능
  3. 구글의 최신화된 VB Engine 이용
  4. 적은 양의 자원으로 일 처리 
  5. 높은 커뮤니티 이용율 및 참여율

### 정리
|`JavaScript`|`Node`|
|------------|--------|
|프로그래밍 언어|브라우저 밖의 자바스크립트 런타임|
|js 자체적으로는 __브라우저__ 에서만 동작<br>`document` 다룸| __데스크탑__ 에서 동작<br>`js`언어로 서버개발 가능하도록 하는 환경|