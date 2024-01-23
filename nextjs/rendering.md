## 렌더링 방식
> [참고자료](https://velog.io/@yena1025/Next.js%EC%9D%98-%EB%8B%A4%EC%96%91%ED%95%9C-%EB%A0%8C%EB%8D%94%EB%A7%81-%EB%B0%A9%EC%8B%9D)

1. SSR
2. CSR
3. 특정 컴포넌트 > 클라이언트 렌더링 방법
4. SSG

### 고민점
- 빌드 시점 > 정적 생성
- 실행 시점 > 동적 제공
### 1. SSR - 윈도우나 브라우저 전용 api 사용 불가 ㅠ,ㅠ
1. 서버에서 전부 렌더링
2. 해당 페이지 자바스크립트 로드
3. 동적 페이지 내용 렌더링 (하이드레이션)

- 예시
  - 모든 글 한 페이지 렌더링하는 경우
- 장점
  - 안정성 증가
  - 웹 사이트 제공 범위 확대
  - 검색엔진최적화 유리

### 2. CSR
1. 자바스크립트 번들 > 서버 전송 > 클라이언트 렌더링
2. 빌드 과정 컴파일 JS, CSS > HTML > `<div id="root"></div>` 렌더링
  - 렌더링 동안 화면 비어있음

### 3. 🔥특정컴포넌트 무조건 브라우저에서 렌더링 방법
- Nextjs 기본 > 리엑트 컴포넌트 서버 렌더링 or 빌드 시점 미리 렌더링
- nodejs런타임 > 브라우저 전용 api / canvas 같으 html요소 제공 > 서버 렌더링 시 실패 처리
#### 3-1. useEffect
#### 3-2. typeof window
```js
// 지금 코드
function IndexPage() {
	const side = typeof window === 'undefined' ? 'server' : 'client';
    
    return <div>현재 {side} 사이드 렌더링 중입니다</div>
}

export default IndexPage;
window 객체가 정의되지 않으면(undefined이면) 서버 사이드,
window 객체가 존재하면(undefined가 아니면) 클라이언트 사이드
```
#### 3-3. 동적 컴포넌트 로딩 (동적 import)
- nextjs 제공 기능
- 컴포넌트를 import 하는 옵션
- 리엑트 하이드레이션까지 끝나야 해당 컴포넌트와 상호작용 가능
### 4. SSG
- 빌드 시점 미리 렌더링
- 매 빌드시 내용 거의 변하지 않는 경우
- 정적 페이지 > 리엑트 하이드레이션 > 사용자와 웹 페이지 간 상호작용 가능
### 5. ISR
- Incremental Static Regeneration 약자
- 정적 페이지 업데이트 후 다시 렌더링할 주기 지정⭐
- 예시
  - 데이터 가져오는데 오래 걸리는 경우 사용
  - 대시보드
  - SSG + ISR 함께 사용
- 🔥SSR + SSG 섞어 쓰는 느낌

