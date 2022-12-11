## Vue.js `webpack` 설정 방법
> [참고자료](https://jw910911.tistory.com/79)

### 1. npm 패키지 모듈 설정
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
