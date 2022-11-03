## E2E TEST 
> `selenium` `nightwatch.js`
- [참고자료](https://kamang-it.tistory.com/entry/NightwatchJavaScript%EC%97%90%EC%84%9C-e2e-Test%ED%95%98%EA%B8%B0-%EC%99%95%EC%B4%88%EB%B3%B4%EB%A7%8C)
- [참고자료](https://blog.coderifleman.com/2016/06/17/e2e-test-and-nightwatch/)

### 1. E2E TEST - 여기서 설명한 부분은 `nigthwatch.js` 테스트 프레임워크 
> 사용자가 사용한다고 가정하는 테스트

- E2E 테스트는 시스템 전반을 테스트하는 **시스템 테스트의 일부**
  - ✔GUI 테스트 필수!
  - 여기서 사용하는 부분이 ? `nightwatch.js` 
#### 1-1. 셀레니움 - 웹브라우저 조작
- ![image](https://user-images.githubusercontent.com/61215550/199640140-6fb35b96-0b21-4b6b-a466-c61266a5039e.png)
- ✔ 셀레니움 드라이버 >> 브라우저 직접 조작
- 어느 부분에서 예상대로 동작 또는 못했는지 파악 가능!


```shell
npm i -g nigthwatch
npm i -D chromedriver
⭐ 셀레니움 서버는 자바로 설치 
```

### 2. [개념] E2E TEST
- **시스템 테스트** 에 속함 
  - 시나리오 테스트
  - 기능 테스트
  - 통합 테스트
  - GUI 테스트
#### 2-1. E2E 테스트 프레임워크 
- 종류 2가지 ⭐
  - 헤드리스 브라우저 의존하는 것들(커멘드 라인 명령어로 조작할 수 있는 **화면이 없는 브라우저**)
  - 셀레니움 웹드라이버 의존하는 것들  


|헤드리스 브라우저|셀레니움 웹드라이버|
|---|-----|
|크로스 브라우징 테스트 ❌|크로스 브라우징 테스트 ⭕|
|Jsdom 기반의 좀비(`Zombie.js`), 웹킷 엔진 기반의 팬텀(`Pantom.js`), 겟코 엔진 기반의 슬리머(`Slimer.js`) 등 존재|`webdriver.io` `Cucumber.js` `프로트랙터` `나이트와치`|
|`assert` ❌|`assert` ⭕|

#### 2-2. [개념] 셀레니움 웹드라이버
- 셀레니움 >> 웹 브라우저를 사용하여 웹 애플리케이션을 테스트하는 오픈 소스 도구! 
- `브라우저 자동화` 

#### 2-3 셀리니움 RC  vs  웹드라이버
> 2011년 7월 셀레니움 웹드라이버(셀레니움 2.0) 릴리즈!! 아래 방식 참고해서 합쳐진거야 오오 - **현재의 셀리니움은 웹드라이버랑 통합된 버전**
|셀레니움 RC|웹드라이버|
|---|---|
|![image](https://user-images.githubusercontent.com/61215550/199641528-ec944ef4-c949-4954-bc39-5a36ea19f437.png)|![image](https://user-images.githubusercontent.com/61215550/199641536-f5e816b4-a270-4e3a-b632-977b13f507bb.png)|

#### 2-4. 셀레니움 서버와 자바스크립트는 서로 잘 안맞음 ㅠ,ㅠ >> 그래서 나온게 `webdriver.io` `나이트왓치` 등
- 돔을 조작하거나 셀렉팅하는데 한계 존재
- 셀레니움 웹드라이버와 노드를 바인딩하여 다양한 기능을 제공하는 여러가지 형태의 프로젝트 생김

#### 2-5 나이트왓치
> [참고자료](https://huns.me/)
- 노드 기반의 E2E 테스트 프레임워크
- 셀레니움 웹드라이버를 중개하여 각종 드라이버를 조작하고 동작이 기대한 것과 일치하는지 테스트


### ⭐결론. 저자의 주관적 의견 >> 프로젝트 저장소에 저장하기 보다는 **별도의 E2E 테스트 저장소 만들어서** 관리가 좋을 듯 싶음!
![image](https://user-images.githubusercontent.com/61215550/199642244-8c80a8ce-ffa6-498a-940e-de0be787a23b.png)

