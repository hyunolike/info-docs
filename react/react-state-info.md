## 리엑트 상태관리 흐름 - 번역
> [참고자료](https://medium.com/@yujso66/%EB%B2%88%EC%97%AD-%EB%A6%AC%EC%95%A1%ED%8A%B8-%EC%83%81%ED%83%9C-%EA%B4%80%EB%A6%AC%EC%9D%98-%EC%83%88%EB%A1%9C%EC%9A%B4-%ED%9D%90%EB%A6%84-6e5ed0022e39)
- 🙄 애플리케이션 커짐에 따라 > 전역 상태 관리 권장!
  - 리엑트는 상태 관리에 대한 확실한 가이드라인 미제공ㅠ,ㅠ
### 🔥전역 상태 관리 라이브러리가 해결하고자하는 문제!!!!!
#### 1. 저장된 상태 컴포넌트 트리 어디서든 읽어오는 기능
- 상태관리 라이브러리 기본 기능
- 실제 저장 > 2가지 주요 접근 방식
  - 리엑트 런타임 내부 `useState` `useRef` `useReducer` 같은 역할
  - 리엑트 외부의 모듈 상태 활용
##### 2. 저장된 상태를 수정하는 기능
- 저장소 > 데이터 읽고 쓰는 `직관적인 API` 제공
- 상태 함수 > 리엑트 UI 모델(참조 평등 + 불변) 업데이트 의존하는 개념 적합 감지 및 리렌더링
  - 😁 자바스크립트 > 변경 가능한 언어
- 리엑트 사용 > 참조 평등 고려
- 🤠개발자 변경 가능한 스타일 코드 작성 가능하도록 > `immer`과 같은 라이브러리 인기 이유
#### 3. 렌더링 최적화하는 메커니즘 제공
- 상태 변경 시 > 재조정 과정 비용 많이 소요
- 큰 앱 > 런타임 성능 저하
- 👨‍🚀상태 업데이트시에만 다시 렌더링!
- `Valtio` > 업데이트 시기 자동 추적 + 컴포넌트 다시 렌더링 시기 자동으로 관리
  - 내부적으로 `proxy` 사용
#### 4. 메모리 사용 최적화하는 메커니즘 제공
- 메모리 적절한 관리 필요
### 🔥 Flux 문제?
#### `작은 규모` 문제
- 상호작용 거의 없는 간단한거에는 과해
#### `큰 규모` 문제 
- 다양한 유형의 상태 존재 ㅠ,ㅠ
  1. 로컬 ui 상태 
  2. 원격 서버 캐시 상태
  3. url 상태
  4. 전역 공유 상태
  5. 기타 (더 구별되는 상태 유형...)
### 상태관리 라이브러리
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/efd7c7c6-b721-4b25-8811-28560c793965)