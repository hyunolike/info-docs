## 자바스크리븥 테스트 도구
> [참고자료](https://velog.io/@rimo09/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%ED%85%8C%EC%8A%A4%ED%8A%B8-%EB%8F%84%EA%B5%AC)
### 1. 테스트 종류
- 범위에 따라
  - `단위`, `통합`, `E2E` 
### 2. 테스트 환경
#### 2-1. 브라우저 환경
- 브라우저 모든 api 사용한 테스트
- 브라우저 호환성 테스트 
- [Karama](https://github.com/karma-runner/karma)(테스트 러너 역할만 수행 - 별도의 테스트 프레임워크 필요), Selenium?
#### 2-2. Node.js 환경
- 실행속도 빠름
- 브라우저 DOM API 사용 불가 >> [JSDOM](https://github.com/jsdom/jsdom) 라이브러리 사용해 브라우저 환경을 가상으로 구현하는 방식
- 브라우저 실행 못해 >> 크로스 브라우징 테스트 불가 ㅠ,ㅠ
- Mocha, Jest, Puppeteer
### 3. 자바스크립트 테스트 도구 ⭐
- ✔ 4가지로 분류
  - `Test Runner`: 테스트 구동할 수 있는 환경 제공
  - `Testing framework`: 테스트 코드 작성을 위한 기반(틀) 제공
  - `Assertion library`
  - `Test Double library`
#### 3-1. Test Runner
- 테스트 파일 읽어 작성한 코드 실행 및 결과 출력
- 파일의 변경된 사항 자동 재실행 `watcher` / 특정 테스트만 실행 / `reporter` 를 지정해 원하는 형태로 결과 출력
- 브라우저: Karma, Selenium?
- Node.js: Jest, Mocha ... 등 >> Node.js 기반의 테스트 러너는 러너의 실행환경과 코드의 실행환경을 구분할 필요 x >> 테스트 프레임워크와 통일된 형태로 제공
#### 3-2. Testing Framework
- 사용자가 테스트 코드 작성할 수 있는 기반 제공해주는 도구
- Jest, Mocha, Jasmine, AVA
### 4. Assertion library
- 테스트 러너에서의 단언(`assertion`) 테스트 통과하기 위한 조건 명확하게 기술하기 위해 사용
- 테스트 프레임워크에서 다양한 방식의 api 기능 제공하지만 >> `mocha` `chai` 와 같은 별도의 단언 라이브러리 사용하도록 권장!
### 5. Test Double library
- 테스트 더블 ✔
  - 테스트 하기 위해 실제 코드 대신에 사용하는 객체/함수
  - 독립적이고 분리된 단위 테스트 위해 외부 의존성을 임의로 주입할 때 사용
  - dummy, fake, stub, mock, spy  등 통칭
### 6. 이외
- 리엑트 컴포넌트 테스트: `react-testing-library` `Enzyme`
- 앵귤러 js 위한 e2e 테스트: `Protractor(Selenium, WebdriverJS기반 구현)`
- E2E 테스트: Cypress, Playwright, NightWatch, TestCafe
