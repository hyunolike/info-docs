## Storybook
> [참고자료](https://www.daleseo.com/storybook/) <br>
> [참고자료](https://velog.io/@katanazero86/react-storybook) <BR>
> [참고자료](https://velog.io/@juno7803/Storybook-Storybook-200-%ED%99%9C%EC%9A%A9%ED%95%98%EA%B8%B0) ✌

- 다양한 방식으로 사용되고 있는 `UI 컴포넌트 개발도구`
- UI 컴포넌트 테스트 및 프로토타이핑 가능 (컴포넌트 단위)
- 디자인 시스템 개발을 위한 도구로도 사용 가능
- 단순하게 사용한다면 샘플코드와 props 등을 정보를 제공하는 용도로도 사용 가능
- 스토북의 기본 구성 단위 >> 스토리 ✔
  - 각 스토리: 해당 ui 컴포넌트가 어떻게 사용될 수 있는지를 보여주는 하나의 예시라고 생각하면 됨!! 

### 1. 사용 이유
- 독립적인 환경에서 UI 컴포넌트 개발 가능
  - 복잡한 데이터나 비즈니스 로직을 구축하지 않아도 됨
- 특정한 스냅샷을 스토리로 만들고 테스트 가능
  - 재사용 위해 만들어진 컴포넌트 >> STORY 조합 >> 특정한 스냅샷 만들어 개발/테스트/QA 활용 가능
- UI 컴포넌트 라이브러리 문서화 / 디자인 시스템을 개발하기 위해 사용 가능
 
### 2. Storybook 세팅
- Add Stroybook `npx sb init`
  - `main.js`: storybook을 위한 config 설정
  - `preview.js`: 해당 프로젝트의 모든 Story에 global하게 적용될 포맷을 세팅하는 곳
