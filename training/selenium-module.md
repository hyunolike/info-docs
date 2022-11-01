## 셀레니움 재사용 가능한 모듈 개발
### 패키지 구조
- lib > config.js / DriverFactory.js
- pages > BasePage.js / *Page.js 
- report > ... (추가 예정)
- test > spec_helper.js / *Test.js

### 구조
![image](https://user-images.githubusercontent.com/61215550/199136101-1edbc40d-2786-4759-8c8e-24eafc110432.png)

### 주요 코드 내용
#### `DriverFactory.js`
```javascript
require('chromedriver');
const { Builder } = require('selenium-webdriver')
const chrome = require('selenium-webdriver/chrome');

/**
 * npm ssl 인증서 필요로 해당 클래스 사용 보류 2022/10/27
 *
 * 구조
 * - build(): 셀레니움 빌드 및 세션 설정
 * - quit(): 셀레니움 종료
 */
class DriverFactory {
    constructor(driver) {
        this.driver = driver;
    }

    async build(){
        const chromeOptions = new chrome.Options();
        chromeOptions.excludeSwitches("enable-logging");

        this.driver = await new Builder().forBrowser("chrome")
            .setChromeOptions(chromeOptions).build();
    }

    async quit(){
        await this.driver.quit();
    }
}

module.exports = DriverFactory;
```

#### `spec_helpler.js`
```javascript
require('chromedriver');
const DriverFactory = require('../lib/DriverFactory');

const driverFactory = new DriverFactory(this.driver);

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
    /**
     * exclude selenium chrome option code
     */
    await driverFactory.build();
    this.driver = driverFactory.driver;
})

/**
 * TODO: this.driver 값 가져오는 방식 구상 필요
 */
afterEach( async function () {
        await driverFactory.quit();
})
```

#### `BasePage.js`
```javascript
const config = require("../lib/config");
const Until = require("selenium-webdriver").until;
const {By} = require('selenium-webdriver');

/**
 * 페이지 UI 테스트 기본값
 * - visit(): test url 설정
 * - find(locator): 해당 주소에 맞는 요소 리턴
 * - click(locator): 해당 요소 클릭
 * - type(locator, inputText): 요소 찾은 다음 해당 값 전송
 * - isDisplayted(locator, timeout)
 *  1. 요소 위치 나타날때까지 기달림
 *  2. 요소 보여짐 나타날때까지 기달림
 *  3. 리턴 투루~
 */

class BasePage {
    constructor(driver) {
        this.driver = driver;
    }

    async visit(url) {
        if(url.startsWith('https')) {
            await this.driver.get(url);
        } else {
            await this.driver.get(config.baseUrl + url);
        }
    }

    find(locator) {
        return this.driver.findElement(By.xpath(`${locator}`));
    }

    async click(locator) {
        await this.find(locator).click()
    }

    async type(locator, inputText) {
        await this.find(locator).sendKeys(inputText);
    }

    // async waitDelay(locator, timeout) {
    //     let by = By.id("ContentPlaceHolder1_spName");
    //     await this.driver.wait(Until.elementIsVisible(locator), timeout);
    //
    //     return ture;
    // }

    // async isDisplayed(locator, timeout) {
    //     if (timeout) {
    //         await this.driver.wait(Until.elementTextContains(
    //             await this.driver.findElement(By.xpath('//*[@id="form1"]/div[6]/div[1]/div/div/section[1]/h1')).getText(),
    //             "로그인"
    //         ), timeout);
    //         await this.driver.wait(
    //             Until.elementIsVisible(this.find('//*[@id="form1"]/div[6]/div[1]/div/div/section[1]/h1')),
    //             timeout
    //         )
    //         return true;
    //     } else {
    //         try {
    //             return await this.find(locator).isDisplayed();
    //         } catch (error) {
    //             return false;
    //         }
    //     }
    // }
}

module.exports = BasePage;
```
