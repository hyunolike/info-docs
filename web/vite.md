## Vite
> [참고자료](https://joshua1988.github.io/vue-camp/vite/intro.html#vite%E1%84%85%E1%85%A1%E1%86%AB)
- 자바스크립트 네이티브 모듈 기반 **데브 서버*
- 😛 현대 프론트엔드 개발 생태계 >> 웹팩 중심 >> 개발 환경 & 배포 시스템 구축!!
  - 비트 사용 이유: 웹팩을 사용할 때보다 훨씬 더 빠르게 개발하고 배포 가능해짐 

### 1. 번들링
- `웹팩` `롤업` `파셀` 과 같은 모듈 번들러 >> 자바스크립트의 모듈화
- (기존) `require.js` 모듈 로더 & `IIFE` 로만 모듈화 가능 ㅠ,ㅠ
- (개선) 모듈화 문법 `import` `export` 등장 !! 🎉 >> 현재 프론트엔드 개발 생태계 `모듈 번들러` 대부분 **웹팩** 사용! 
 - 모듈화 문법 >> 여러 개의 파일을 하나로 합쳐주거나 의미 있는 단위로 묶어 주는 것 >> 번들링!! 

### 2. ESM (자바스크립트 네이티브 모듈) 
- 모듈화 문법 ❌ >> 브라우저 자체에서 소화해 낼 수 있는 모듈 방식!
  - 브라우저에서 자체 소화 가능!! ⭐️


```html
<script type="module" src="./app.js"></script>
```


### 3. Vite(비트) 특징
- 로컬에서 번들링 사용 x >> 로컬 서버 구동 속도 매우 빨라
- 번들링 하지 않고! 서버를 실행하기 때문 명령어를 실행함 + 서버 바로 구동!


```js
// vite.config.js
module.exports = defineConfig({
  build: {
    rollupOptions: {
      // https://rollupjs.org/guide/en/#big-list-of-options
    }
  }
})
```


### 4. 비트 시작 방법
```shell
npm init vite@latest my-vite
```
