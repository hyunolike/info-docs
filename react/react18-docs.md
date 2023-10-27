## ⭐`React 18` 공식문서 보기이이이 updated by `2023/10/27`
> [공식문서](https://react.dev/reference/react)

### 1. React Hooks 내장함수
#### 1-1. 종류 (6가지 정도 크게)
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
#### 1-2. 다른 Hooks 
> 최종 출시된것만 파악
##### a. `useDeferredValue`
- UI 일부 업데이트 지연!
- 최상위 컴포넌트에서 사용
##### b. `useId`
- 접근성 속성에 전달할 수 있는 고유ID 생성
##### c. `useImperativeHandle`
- ref??? 노출된 핸들을 사용자 정의할 수 있다??
##### d. `useInsertionEffect`
- `CSS-in-JS` 라이브러리 위한 거
- 레이아웃 효과가 실행되기 전 DOM 요소 삽입 가능
##### e. `useLayoutEffect`
- 성능 저하ㅠㅠ 가능하면 `useEffect` 사용!
- `useEffect` > 브라우저가 화면을 다시 그리기 전 실행되는 버전
##### f. `useSyncExternalStore`
- 외부 저장소 구독 가능!
  - 외부 저장소 구독
  - 브라우저 api 구독
  - 커스텀 훅 로직 추출
  - 서버 렌더링 지원 추가
### 2. Components
#### 2-1. `<Fragment>` `<>...</>`
- 단일 요소 필요한 경우 > 요소 래핑 + 그룹화
#### 2-2. `<Profile>` 
- 프로그래밍 방식 > React 트리의 렌더링 성능 측정
#### 2-3. `<StricMode>`
- 개발 초기에 구성 요소의 일반적인 버그 찾기!
#### 2-4. `<Suspense>`
- 하위 항목이 로드를 완료할 때까지 대체 표시!
### 3. 내장 React API
> [공식문서](https://react.dev/reference/react/apis)
#### 3-1. `createContext`
- `useContext` 함께 사용
#### 3-2. `forwardRef`
- 구성 요소 > 참조 이용 > dom 노드 상위 구성 요소에 노출
#### 3-3. `lazy`
- 처음 렌더링 끝날떄까지 > 구성 요소의 코드 로드 연기!
#### 3-4. `memo`
- 소품?? 변경되지 않은 경우 > 구성 요소를 다시 렌더링하는 것 건너뛰기
#### 3-5. `startTransition`
- ui 차단 x > 상태 업데이트 가능
