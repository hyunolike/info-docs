## Vue.js `webpack` 설정 방법 - [중요 참고자료](https://happy-jjang-a.tistory.com/124)
> [참고자료](https://jw910911.tistory.com/79)
- 🎉 vue cli 통해 프로젝트 생성 시 >> 웹팩 자동 적용 >> `npm run serve` `npm run build` 모두 웹팩기반으로 동작!!!
- `vue cli 2.x` >> `webpack.config.js` 
- `vue cli 3.x` >> `vue.config.js` 
### 🦁 Webpack
- 모듈 간의 관계를 해석해 정적인 자원으로 변환시켜주는 도구
- 어플리케이션 동작 관련된 `html` `css` `js` `img` >> **1개의 js 파일** 로 변환!! 😛
- <img width="792" alt="image" src="https://user-images.githubusercontent.com/61215550/206890854-c01dedbc-7667-416a-aeaa-f6b1b45e1046.png">



### npm 패키지 모듈 설정
- webpack 설정 
  - `webpack` `webpack-cli` `vue-loader` `vue-template-compiler` npm 설치 진행!
- ✅ `vue-template-compiler` === `vue` 버전은 항상 일치 시켜줘야 함!!!!


```json
{
  "name": "number-baseball",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "build": "webpack"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "vue": "^2.6.10" 😛
  },
  "devDependencies": {
    "vue-loader": "^15.7.2",
    "vue-template-compiler": "^2.6.10", 😛
    "webpack": "^4.41.2",
    "webpack-cli": "^3.3.10"
  }
}
```
