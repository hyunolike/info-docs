## next.js 13
> [참고자료](https://velog.io/@yoosion030/Next.js-13-%EC%A0%95%EB%A6%AC)


```
app/디렉토리(Beta)
레이아웃
React 서버 컴포넌트
스트리밍
Turbopack(alpha)
next/image(안정적)
@next/font(beta)
상향된 next/link
```

### app/Directory
- Nextjs 사랑받는 기능 중 하나 >> 😛`파일 시스템 라우터`
  - 폴더 안에 파일 생성 시 애플리케이션 즉시 경로 생성
- `Next 13` 에서 app/ 디렉토리 도입 
  - 레이아웃: 경로간 UI를 쉽게 공유
  - 스트리밍: 로딩 상태 표시 및 렌더링되는 ui 단위로 스트리미 
  - 서버 컴포넌트
  - 데이터 가져오기

#### 버전별 비교
|13 이하|13|
|---|----|
|![image](https://user-images.githubusercontent.com/61215550/212236052-b15f0ef2-6cc5-47ef-8685-0d64ab0e8a83.png)|![image](https://user-images.githubusercontent.com/61215550/212236010-701b1fd6-69cb-4d99-88a0-1a18cacd7426.png)|
