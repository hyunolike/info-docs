## swiper 기본 사용 방법
> [참고자료](https://swiperjs.com/)

### 1. 사용 순서
1. npm 다운로드 (`23.12.28 기준` / swiper element 사용 권장 중)
2. `_app.js` 내 아래 코드 적용


```js
// import function to register Swiper custom elements
import { register } from 'swiper/element/bundle';
// register Swiper custom elements
register();
```


3. `index.js` > css 파일 추가 `swiper.css` 직접 추가
4. 아래 코드 사용


```js
<swiper-container>
  <swiper-slide>Slide 1</swiper-slide>
  <swiper-slide>Slide 2</swiper-slide>
  <swiper-slide>Slide 3</swiper-slide>
  ...
</swiper-container>
```
