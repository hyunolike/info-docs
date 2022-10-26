## Selenium 테스트 제목 등 가져오는 방법
> [참고자료](https://stackoverflow.com/questions/22643924/get-test-title-and-state-in-selenium-webdriver-js-testing)
- ✔ `Mocha` 에서 제목 및 상태와 같은 현재 테스트 정보 얻을 수 있음


```javascript
/**
 * 테스트 기본값 설정
 * - beforeEach()
 *  1. 테스트 제목 가져오기
 *  2. 셀레니움 빌드 시작
 *  3. 셀레니움 드라이브 변수 저장
 *
 * - afterEach()
 *  1. 테스트 상태 가져오기
 *  2. 테스트 상태에 따른 종료!
 */

beforeEach(async function () {
    const testName = this.currentTest.fullTitle()
    await driverFactory.build(testName);
    this.driver = driverFactory.driver;
})

afterEach(async function () {
    const testPassed = this.currentTest.state === 'passed';
    await driverFactory.quit(testPassed);
})
```
