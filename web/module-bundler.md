## 모듈 & 번들러
> [참고자료](https://velog.io/@sunhwa508/%EB%AA%A8%EB%93%88-%EB%B2%88%EB%93%A4%EB%9F%AC-webpack)
### 모듈 시스템
- `AMD`
  - Asynchronous Module Definition 비동기 방식
  - `define()` `require()` 사용 방식
  - 대표적 `RequireJS`
- `CommonJS`
  - Nodejs
  - `require`, `module.exports` 사용 방식
- `ES6` (ES2015)
  - `import` `export` 방식
  - 브라우저 지원 x > `Babel` `@babel/plugin-transform-modules-commonjs` 통해 컴파일
### 번들러
- 대표적 예. 웹팩, 파셀
- ✔ 의존성 있는 모듈 코드 > 하나(여러개) 파일로 만들어 주는 도구
  - 브라우저 환경 잘 실행 > 가공해주는 역할
#### 1. 잚만든 모듈
- 파일 > 하나의 scope 되도록 구현
#### 2. 번들러 이점
- 자바스크립트 파일 > 기능 단위 모듈화 > 묶어 관리!
- 번들러 사용 > 소스코드를 모듈별로 작성
- 모듈간 혹은 외부 라이브러리 의존성 쉽게 관리
#### 3. 종류
- `webpack` `RequireJS` `Browserify` `Rollup` `Parcel`
#### 4. 번들러 없이 모듈 사용하는 방법
- `commonJS` `AMD` `ES2015` 모듈화 시스템 사용 가능
