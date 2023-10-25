## `RSC` 리엑트 서버 컴포넌트
> [참고자료](https://pyjun01.github.io/v/rsc/) <br/>
> [참고자료22](https://velog.io/@gouz7514/react-RSC-feat.NextJS)
- ⭐ 리엑트 RSC > NEXT 통해 릴리즈!
- client + server 의 장점 모두 채택한 새로운 개념
- 서버에서 한 차례 렌더링 거친 뒤 클라이언트로 전달!

### 1. 사용 이유
- 서버 인프라 효과적 활용
  - js 번들 의존성 유지 및 성능 향상
- 로딩 속도 향상
- 클라이언트 사이드 js 번들 크기 감소
- ...
#### 1-1. 클라이언트 중심 앱(서버 사용의 결핍)
- 클라이언트에서 발생하는 문제 서버에서 쉽게 해결가능하지만 한계..
### 2. RSC 지탱하는 기술
#### 2-1. SSR
1. 서버에서 react app 실행 `html 응답`
2.  클라이언트에서 html 응답받아 react app js 번들 `로딩`
3. 번들  react app 재실행 > `hydrate` 처리
#### 2-2. Concurrent Rendering
- react render 작업 잘게 나누고
- 우선순위 부여해 render 작업을 react가 직접 제어(중단, 재개, 파기) 할 수 있는 형태
  - 기존에는 `동기식 렌더링 방식` > 한번 렌더하면 못 멈춰 ㅋㅋㅋ
#### 2-3. Streaming SSR
- 기존 `동기식 렌더링 방식` > 전체 트리 처리해야 돼(폭포수 처럼)
- 트리별로 나눠서 SSR 진행
#### 2-4. Suspense
- 데이터 로딩 끝날 때까지 자식 렌더 미뤄
### 3. ⭐리엑트 서버 컴포넌트
- 서버에서 실행되는 컴포넌트


|기존|변경|
|-|-|
|![image](https://github.com/hyunolike/info-docs/assets/61215550/15d5aa20-8529-49c7-8620-39b79d130db6)|![image](https://github.com/hyunolike/info-docs/assets/61215550/b94b8cc7-4d41-4e23-a2a7-2bd2ccf75f46)|
