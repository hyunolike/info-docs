## nextjs 환경변수 설정방법
> [참고자료](https://velog.io/@with-key/Next.js-%ED%99%98%EA%B2%BD%EB%B3%80%EC%88%98%EA%B0%80-undefined-%EC%9D%BC-%EB%95%8C)

- nextjs 환경변수 설정
  - `process.env.NEXT_PUBLIE_변수명`
- (참고) nodejs 환경변수 설정
  - `process.env.변수명`
 ### ⭐`프론트엔드`에서 얻을 수 있는 환경 변수 설정 방법 (추가. next.config.js 설정필요)
- 최신버전에서는 `NEXT_PUBLI_` 이것만 추가하면 밑에 추가하지 않아도 사용 가능!

 
```
const nextConfig = {
  env:{
    API_KEY: process.env.API_KEY
  }
}`

```
### 💡 `dotnet` 라이브러리 사용
> [참고자료](https://intrepidgeeks.com/tutorial/setting-environment-variables-env-in-nextjs#:~:text=Next.js%EC%97%90%EC%84%9C%20%ED%99%98%EA%B2%BD%20%EB%B3%80%EC%88%98%EB%A5%BC%20%EC%96%B4%EB%96%BB%EA%B2%8C%20%EC%82%AC%EC%9A%A9%ED%95%A9%EB%8B%88%EA%B9%8C%3F%20%EB%8B%A8%EC%88%9C%ED%95%9C%21%20Next.js%20%EC%95%A0%ED%94%8C%EB%A6%AC%EC%BC%80%EC%9D%B4%EC%85%98%EC%9D%98,%EA%B7%B8%EB%9F%B0%20%EB%8B%A4%EC%9D%8C%20%EC%BD%94%EB%93%9C%EC%97%90%EC%84%9C%20%EC%9D%B4%EB%9F%AC%ED%95%9C%20%EB%B3%80%EC%88%98%EB%A5%BC%20%EC%B0%B8%EC%A1%B0%ED%95%A0%20%EC%88%98%20%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4.)
