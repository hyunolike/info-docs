## nextjs 환경변수 설정방법
> [참고자료](https://velog.io/@with-key/Next.js-%ED%99%98%EA%B2%BD%EB%B3%80%EC%88%98%EA%B0%80-undefined-%EC%9D%BC-%EB%95%8C)

- nextjs 환경변수 설정
  - `process.env.NEXT_PUBLIE_변수명`
- (참고) nodejs 환경변수 설정
  - `process.env.변수명`
 ### ⭐`프론트엔드`에서 얻을 수 있는 환경 변수 설정 방법 (추가. next.config.js 설정필요)
```
const nextConfig = {
  env:{
    API_KEY: process.env.API_KEY
  }
}`

```
