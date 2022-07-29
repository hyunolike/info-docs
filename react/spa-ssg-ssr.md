## SPA SSG SSR 
> [참고자료](https://www.daleseo.com/spa-ssg-ssr/)

### SPA
> Single Page Application
- 단일 웹페이지로 돌아가는 애플리케이션
- 자바스크립트 이용 >> 단일 웹페이지 상의 HTML 요소 동적으로 생성, 조작
- 최초 로딩시간 오래 걸릴수 있음 ㅠ,ㅠ
- `SEO(검색 엔진 최적화)` 불리 ㅠ,ㅠ
- 크롤러 `crawler` 웹페이지에서 읽어갈 수 있는 내용 `<div>` 요소 밖에 없기에...

### SSG
> Static Site Generator
- 정적 사이트 생성기로 번역할 수 있는 SSG
- 항상 동일한 페이지 보여주는 거 `Gatsby` `Hugo` `Jekyll` `Hexo`
- SEO 좋음

### SSR
> Server-Side Rendering
- 말 그대로 서버측에서 웹페이지 랜더링하는 기술
- SSG와 다른점은 !! 
  - 빌드 타임에 웹사이트 전체 미리 만들어 놓는 거 아님!!
  - 클라이언트로부터 요청 들어올때마다 실시간으로 해당 웹페이지 만들어냄
  - E-commerce, SNS 매우 적합
- ⭐SPA 개발에 사용 가능한 SSR 프레임워크 

|SPA|프레임워크|
|---|----------|
|React|`Next.js` `Remix`|
|Svelte|`SvelteKit`|
|Vue.js|`Nuxt.js`|
