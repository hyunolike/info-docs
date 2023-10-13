## `next.js` 13버전
> [참고자료](https://torimaru.tistory.com/42)
- 13버전 > 모든 reeact 컴포넌트 `서버사이드 컴포넌트`
### layout
- 기존 `_app.tsx` `_document.tsx` 역할
- app 폴더 아래 > `layout.tsx` 필수
### head
- 각 라우팅마다 title 다르게 설정 가능
- 라우팅 되지 않음
  - 무조건 폴더 밑 첫 `page.tsx` 파일 첫번째로
### ✔ data fetching
- `react suspense` 기반 새로운 방식
- 기존엔 export > 서버사이드 단에서 돌아가는 방식으로 개발 > getServerSideProps, getStaticProps
- 13버전에서 사용하는 방법


```js
  // This request should be cached until manually invalidated.
// Similar to `getStaticProps`.
// `force-cache` is the default and can be omitted.
fetch(URL, { cache: 'force-cache' });

// This request should be refetched on every request.
// Similar to `getServerSideProps`.
fetch(URL, { cache: 'no-store' });

// This request should be cached with a lifetime of 10 seconds.
// Similar to `getStaticProps` with the `revalidate` option.
fetch(URL, { next: { revalidate: 10 } });
```
#### ✔ `force-cache` 디폴트값
- 캐시 강제 > 정적 사이트 생성
- 처음 `서버 사이드` > 이후 `캐시` 된 값 불러오는 형식
#### ✔ `no-store` 옵션
- 캐시 생성 x > 무조건 `서버사이드` 동작
- `no-cache`
#### ✔ `revalidate` 옵션
- ISR
  - SEO 유리
  - 미리 렌더링 > 캐시 > 매우 빠름
  - 내용 변경되도 다시 배포 안해도됨!
#### ✔ `Turbopack`
- Rust 기반 새로운 번들러
- 웹팩의 700배 빠름
#### ✔ `font` 최적화
- 글꼴 자동으로 최적화
- 개인 정보 보호 및 성능 향상 > 외부 네트워크 요청 제거
- 모드 글꼴 파일 > 자체 호스팅
#### ✔ `<Link>`
- `<a>` 없이 사용
