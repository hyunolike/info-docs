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

### 1. app/Directory
- Nextjs 사랑받는 기능 중 하나 >> 😛`파일 시스템 라우터`
  - 폴더 안에 파일 생성 시 애플리케이션 즉시 경로 생성
- `Next 13` 에서 app/ 디렉토리 도입 
  - 레이아웃: 경로간 UI를 쉽게 공유
  - 스트리밍: 로딩 상태 표시 및 렌더링되는 ui 단위로 스트리미 
  - 서버 컴포넌트
  - 데이터 가져오기
- ![image](https://user-images.githubusercontent.com/61215550/212236291-0b1383ad-d7f6-4883-8718-a0ccbfb9cfad.png)
- `app/` 폴더 >> 복잡한 인터페이스 배치하는 것 쉽게 해줌! 
  - 값비싼 재렌더링 방지 >> 라우팅 패턴 가능하게끔!
#### 버전별 비교
|13 이하|13|
|---|----|
|![image](https://user-images.githubusercontent.com/61215550/212236225-24f1a586-cf52-4bc6-ab77-572bec3bc2cd.png)|![image](https://user-images.githubusercontent.com/61215550/212236010-701b1fd6-69cb-4d99-88a0-1a18cacd7426.png)|

### 2. 레이아웃
- `app/` 폴더에서 라우팅하려며  `page.js` 라는 단일 파일 필요
- 여러 페이지 간에 UI 공유 가능
  - 다시 렌더링 X / 레이아웃 상태 유지 및 상호작용
