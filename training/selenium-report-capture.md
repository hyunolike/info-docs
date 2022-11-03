## 셀레니움 이용해 E2E 테스트 진행하고 결과 실패 시, 캡쳐가 포함된 결과 파일을 만들자
### 1. 패키지 구조 :)
![image](https://user-images.githubusercontent.com/61215550/199659403-42356614-6535-4b92-9ceb-1dd18f56642b.png)

### 2. 전체 로직
![모나UI_테스트_동작_로직](https://user-images.githubusercontent.com/61215550/199659442-2fe91d83-2d49-4244-b184-d1ff9fd54e72.png)

### 3. 코드
#### 3-1. lib 패키지
##### `DriverFactory.js`
```javascript
require('chromedriver');
require('selenium-webdriver')
const { Builder } = require('selenium-webdriver')
const chrome = require('selenium-webdriver/chrome');
const conf = require('../conf/conf').config
/**
 * 구조
 * - build(): 셀레니움 빌드 및 세션 설정
 * - quit(): 셀레니움 종료
 */
class DriverFactory {
    constructor(driver) {
        this.driver = driver;
    }

    async build(){
        // 크롬 드라이버 에러 메시지 삭제를 위한 코드
        const chromeOptions = new chrome.Options();
        chromeOptions.excludeSwitches("enable-logging");

        let caps = conf.capabilities;
        this.driver= await new Builder()
            .usingServer(process.env.GRID_HOST)
            .forBrowser('chrome')
            .withCapabilities(caps)
            .setChromeOptions(chromeOptions)
            .build();
    }

    async quit(){
        await this.driver.quit();
    }
}

module.exports = DriverFactory;
```

##### `config.js`
```javascript
/**
 * 테스트에 필요로 한 URL, LOGIN 등 관리하는 파일
 * - 로그인 계정: 박희수 매니저
 */
module.exports = {
    // 모나 테스트에 필요한 정보 관리 영역
    'MONA_WEB_INFO': {
        'BASE_URL': 'https://mobilemona.co.kr',
        'BROWSER': 'chrome',
    },
    // 각 페이지 URL 관리 영역
    'MONA_PAGE_URL': {
        'MAIN_PAGE': '/',
        'LOGIN_PAGE': '/view/login.aspx'
    }
}
```
##### `xpath.js`
```javascript
/**
 * css, id, class 명으로 선택이 어려운 요소를 xpath를 통해 관리하는 파일
 */
module.exports = {
    'LOGIN_PAGE_XPATH' :{
        'LOGIN_TITLE': '//*[@id="form1"]/div[6]/div[1]/div/div/section[1]/h1',
        'USERNAME_INPUT': '//*[@id="ContentPlaceHolder1_txtId"]',
        'PASSWORD_INPUT': '//*[@id="ContentPlaceHolder1_txtPass"]',
        'LOGIN_BUTTON_PATH': '//*[@id=\"ContentPlaceHolder1_btnLogin\"]'
    },
    'MAIE_PAGE_XPATH' :{
        // 메인 페이지 경로
    }
}
```
##### 3-2 pages 패키지
###### `BasePage.js`
```javascript
const CONFIG = require("../lib/config");
const Until = require("selenium-webdriver").until;
const {By} = require('selenium-webdriver');

/**
 * 페이지 UI 테스트 기본값
 * - visit(): test url 설정
 * - find(locator): 해당 주소에 맞는 요소 리턴
 * - click(locator): 해당 요소 클릭
 * - type(locator, inputText): 요소 찾은 다음 해당 값 전송
 */

class BasePage {
    constructor(driver) {
        this.driver = driver;
    }

    async visit(url) {
        if(url.startsWith('https')) {
            await this.driver.get(url);
        } else {
            await this.driver.get(CONFIG.MONA_WEB_INFO.BASE_URL + url);
        }
    }

    find(locator) {
        return this.driver.findElement(By.xpath(locator));
    }

    async click(locator) {
        await this.find(locator).click()
    }

    async type(locator, inputText) {
        await this.find(locator).sendKeys(inputText);
    }
}

module.exports = BasePage;
```

##### `LoginPage.js`
```javascript
require('./spec_helper');
const LoginPage = require('../pages/LoginPage')
const assert = require('assert');
const CONFIG = require('../lib/config.js')
const {By} = require('selenium-webdriver');
const Until = require("selenium-webdriver").until;
const addContext = require('mochawesome/addContext');
const fs = require('fs');


describe('Login', function () {
    let login;

    beforeEach(async function () {
        login = new LoginPage(this.driver);
        await login.load();

    })

    /**
     * 동작 설명
     * - 각 테스트가 끝나면 테스트 실패 여부에 따라 아래 캡쳐 코드가 실행됨
     */
    afterEach(async function () {
        let filename;
        if(this.currentTest.isFailed()){
            var data= await this.driver.takeScreenshot();

            this.driver.takeScreenshot().then(
                function (image){
                    var date = new Date().toISOString();
                    filename = 'out' + date + '.png'; //create file name with timestamp attached

                    fs.writeFileSync('error_screenshot.png', image, 'base64');
                }
            )

            addContext(this, '../error_screenshot.png')
        }
    })

    /**
     * 값 가져올 때 주의사항
     * - 아래 처럼 wait() 함수로 일정 시간 동안 해당 요소 가져오는지 확인
     * - 모든 코드에는 await를 걸어준다!
     */
    it('with valid credentials', async function () {
        await login.authenticate(CONFIG.MONA_WEB_INFO.USERNAME,CONFIG.MONA_WEB_INFO.PASSWORD);
        let by = By.id("ContentPlaceHolder1_spName");
        await this.driver.wait(Until.elementLocated(by, 10000));
        let el = await this.driver.findElement(by);
        await this.driver.wait(Until.elementIsVisible(el), 10000);
        let value = await el.getText();

        assert.equal(value, "박희수");
        // 테스트 실패 케이스
        // assert.ok(false, 'Assert Failed!');
    })
})
```

#### 3-3. test
##### `spec_helper.js`
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
 * 실패 시
 * 1. 해당 실패 부분 스크린 샷
 * 2. 종료()
 */
afterEach( async function () {
    await driverFactory.quit();
})
```
##### `LoginTest.js` 
```javascript
require('./spec_helper');
const LoginPage = require('../pages/LoginPage')
const assert = require('assert');
const CONFIG = require('../lib/config.js')
const {By} = require('selenium-webdriver');
const Until = require("selenium-webdriver").until;
const addContext = require('mochawesome/addContext');
const fs = require('fs');


describe('Login', function () {
    let login;

    beforeEach(async function () {
        login = new LoginPage(this.driver);
        await login.load();

    })

    /**
     * 동작 설명
     * - 각 테스트가 끝나면 테스트 실패 여부에 따라 아래 캡쳐 코드가 실행됨
     */
    afterEach(async function () {
        let filename;
        if(this.currentTest.isFailed()){
            var data= await this.driver.takeScreenshot();

            this.driver.takeScreenshot().then(
                function (image){
                    var date = new Date().toISOString();
                    filename = 'out' + date + '.png'; //create file name with timestamp attached

                    fs.writeFileSync('error_screenshot.png', image, 'base64');
                }
            )

            addContext(this, '../error_screenshot.png')
        }
    })

    /**
     * 값 가져올 때 주의사항
     * - 아래 처럼 wait() 함수로 일정 시간 동안 해당 요소 가져오는지 확인
     * - 모든 코드에는 await를 걸어준다!
     */
    it('with valid credentials', async function () {
        await login.authenticate(CONFIG.MONA_WEB_INFO.USERNAME,CONFIG.MONA_WEB_INFO.PASSWORD);
        let by = By.id("ContentPlaceHolder1_spName");
        await this.driver.wait(Until.elementLocated(by, 10000));
        let el = await this.driver.findElement(by);
        await this.driver.wait(Until.elementIsVisible(el), 10000);
        let value = await el.getText();

        assert.equal(value, "박희수");
        // 테스트 실패 케이스
        // assert.ok(false, 'Assert Failed!');
    })
})
```
#### 3-4. conf
##### `conf.js`
```javascript
require('dotenv').config()
exports.config = {
    LT_user: process.env.LT_user,
    LT_pass:process.env.LT_token,
    capabilities: {
        'build': 'Mocha-Selenium-Sample', //Build name
        'name': 'Test sample for Mochawesome', // Test name
        'platform': 'Windows 10', // OS name
        'browserName': 'chrome', // Browser name
        'version': 'latest', // Browser version
        'visual': false,  // To take step by step screenshot
        'network': false,  // To capture network Logs
        'console': true, // To capture console logs.
        'tunnel': false // If you want to run the localhost then change it to true
    }
}
```

#### 3-5. `.mocharc.js`
```javascript
module.exports = {
    reporter: 'node_modules/mochawesome',
    'reporter-option': [
        'overwrite=true',
        'reportTitle=[status]_[datetime]-[name]-report',
        'showPassed=false',
        'timestamp=longDate',
        'code=false'
    ],
}
```

### `package.json`
```json
{
  "name": "hhjang",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "directories": {
    "test": "mocha"
  },
  "scripts": {
    "test": "mocha --parallel test/*Test.js",
    "testReport": "mocha ----parallel test/*Test.js --reporter mochawesome --parallel",
    "testFeat": "mocha test_feature/*.js"
  },
  "mocha": {
    "timeout": 60000
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "assert": "^2.0.0",
    "chromedriver": "^106.0.1",
    "dotenv": "^16.0.3",
    "mocha": "^7.2.0",
    "selenium-webdriver": "^4.1.2"
  },
  "devDependencies": {
    "mochawesome": "^7.1.3"
  }
}

```
