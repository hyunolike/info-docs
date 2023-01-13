## Next.js 랜더링 과정
> [참고자료](https://www.howdy-mj.me/next/hydrate)

### React vs Nextjs
|React|Nextjs|
|----|----|
|![image](https://user-images.githubusercontent.com/61215550/212217579-18e03f8d-71f1-432d-8ff2-a1d2d1728638.png)|![image](https://user-images.githubusercontent.com/61215550/212217595-9a17cb87-b982-415e-aef1-a5117a14c0e3.png)|

### ✔ Next.js 랜더링
- 2가지 방식 `HTML 생성 시점에 따라 달라짐`
  - `SSG(Static-site Generation)`: 빌드 타임 >> html 생성 >> 매 요청마다 재사용 ex. 블로그, 메뉴얼(바뀌지 않는 페이지에 주로 사용)
  - `SSR`: 매 요청마다 HTML 생성!
- 😛기본적으로 `SSG` 사용! >> `SEO` 유리!
