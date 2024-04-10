## 크로스브라우징 중요성과 해결방법
> [참고자료](https://velog.io/@hyebinee/%ED%81%AC%EB%A1%9C%EC%8A%A4%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A7%95cross-browsing%EC%9D%98-%EC%A4%91%EC%9A%94%EC%84%B1%EA%B3%BC-%ED%95%B4%EA%B2%B0%EB%B0%A9%EB%B2%95)
### 정의
- 웹페이지 제작 시 `모든 브라우저` 깨지지 않고 의도한 대로 (호환성) 나오게 하는 작업
- `W3C` 웹 규격에 맞는 표준 웹 기술을 적용 > 모든 브라우저, 기기에서 사이트가 의도한 대로 보여지게 해야됨!
- 브라우저마다 렌더링 엔진이 다르기 때문

### 브라우저간 호환성 보장방법
1. Don't Repeat Yourself
  - 정보의 반복 줄이기
  - 코드 단순하고 재사용 가능하도록
  - 문제 발생시 대응 좋음
2. DOCTYPE 정의
  - html 어떤 버전으로 작성되었는지 미리 선언 > 웹브라우저가 내용을 올바르게 표시 가능!
  - 선언하지 않으면 호환모드 -> 깨지지 않기위해 각 브라우저마다 다르게 보여질 수 있다!
3. 코드 유효성
  - 코드 유효성 검사
4. css 초기화
  - 브라우저가 제공하는 기본값 존재 이를 제거
5. css 속성에 대한 지원 검토
6. vender prefix
7. 반응형 웹사이트 만들기
  - viewport
  - charset

### Next.js ...
> [공식문서](https://nextjs.org/docs/architecture/supported-browsers)

- broswerlist
- Next.js는 Chrome 64+, Edge 79+, Firefox 67+, Opera 51+, Safari 12+ 등 구성 없이 최신 브라우저를 지원합니다. package.json 파일의 Browserslist 구성을 사용하여 특정 브라우저나 기능을 대상으로 지정할 수 있습니다. 기본적으로 Next.js는 다음 Browserslist 구성을 사용합니다.
