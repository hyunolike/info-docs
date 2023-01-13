## Next.js `SSR` `SPA`
> [참고자료](https://dodody.github.io/pages/techDic-2-Nextjs-SSR-%EA%B7%B8%EB%A6%AC%EA%B3%A0-SPA/)
- ![image](https://user-images.githubusercontent.com/61215550/212215574-e6212739-fcaa-4567-8edb-cc9ee6b966b4.png)

### 1. Nextjs란
> SPA 장점 + SSR 장점 / `page` 기반 빌드!
- `SPA` 인 리엑트에서 `SSR` 을 할 수 있게 구현 되어있는 프레임워크
- ⭐첫 페이지(서버 사이드 렌더링) >> 그 뒤 라우팅(클라이언트 사이드 렌더링) 으로 첫 페이지 내용 모두 채워져 있는 html 받고 이후에는 interaction이 가능한 js 파일은 따로 load해서 클라이언트에서는 DOM을 그대로 그리기만 하면 된다.
### 2. SSR & SPA
- SPA >> CSR
  - 전체 JS 다운로드 >> 초기 렌더링 오래 걸림
  - 해당 페이지의 원하는 데이터만 보여줌 
  - 웹크롤러 봇 >> html에서만 콘텐츠 수집 ㅠ,ㅠ
