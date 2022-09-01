## 리엑트 자동이 아닌 수동으로 Webpack babel 설정 - 스프링에서의 `Profile` 개발환경 설정하는거랑 비슷 ✔
> [참고자료](https://juni-official.tistory.com/158)
### 1. Webpack 개념(번들러)
- 규모 큰 파일들의 의존성 관계를 정리 및 죄적화, jsx 파일을 합쳐 하나의 자바스크립트로 만들어줌 
- 번들러: 여러개의 파일을 모듈화해서 하나의 파일로 묶어주는 도구
  - `webpack`
  - `parcel`
  - `browserify`
  - `vite`
- 엔트리 지점을 정해서 그것과 연관된 모든 파일을 찾아서 묶어줌!

#### 1.1 Webpack 4가지 핵심
> [참고자료](https://365kim.tistory.com/35)
- `Entry`
- `Output`
- `Loader`
- `Plugin`

### 2. 수동 설치 이유
- `CRA` 사용 시 추후 개발환경에 문제 발생 >> webpack 수정 어려움 ㅠ,ㅠ

### 3. 사용 방법
1. `webpack` + `plugin` 설치
2. ... 나머지 설정
3. ⭐ `npx webpack  --mode development`
