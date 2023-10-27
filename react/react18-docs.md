## ⭐`React 18` 공식문서 보기이이이
> [공식문서](https://react.dev/reference/react)

### 1. React Hooks 내장함수
#### 1-1. 종류
##### 상태 Hooks
- 사용자 입력과 같은 정보 기억!
  - `useState`
  - `useReducer`: 리듀서 함수 내부의 업데이트 로직이용해 상태 변수 선언
##### context Hooks
- 정보 `props`로 전달하지 않고도 `부모`로부터 정보 받을 수 있음
  - `useContext`
##### Reference(참조) Hooks  
- 기억하길 원하지만 새 랜더링으로 트리거하는 것을 원하지 않는 경우!
##### Effect Hooks
- 외부시스템에 연결하고 동기화
##### Performance(성능) Hooks
- 최적화 > 불필요한 작업 건너뛰기
- 이전 렌더링 이후 데이터가 변경되지 않는 경우 > 계산 재사용! 재렌더링 건너뛰기!
  - `useMemo`: 비용이 많이 드는 계산 결과 캐시
  - `useCallback`: 함수 정의를 최적화된 구성 요소에 전달하기 전에 캐시!
##### Resource Hooks 
- 리소스를 상태의 일부로 포함하지 않고도 구성 요소에 리소스 엑세스
