## 이벤트 객체  `e`
> [참고자료]([https://365kim.tistory.com/62](https://ko.javascript.info/introduction-browser-events))

- 이벤트 객체 >> 이벤트 발생시킨 요소 + 이벤트에 대한 정보
  - 이벤트 헨들러의 첫 번째 인자
### 종류
- `e.currentTarget`: 핸들러를 할당받은 요소 `this`
- `e.target`: 실제 발생한 노드
- `e.type`: 브라우저 이벤트 종류
- `e.key`: key값을 문자열로 나타냄
- `e.defaultPrevented`: preventDefualt 호출여부
- `e.preventDefault()`: 기본으로 실행되는 이벤트 취소함
