## `immer.js`
> [공식문서](https://immerjs.github.io/immer/) <br/>
> [참고자료](https://kyounghwan01.github.io/blog/React/immer-js/#immer-js%E1%84%85%E1%85%A1%E1%86%AB)
- 리엑트 불변성 유지하는 코드 쉽게 해주는 라이브러리
- 리엑트 컴포넌트 유지(기본속성) 개념

### 리엑트 기본 속성
- 리렌더링 (DOM에서만 이뤄짐!)
  - 부모 컴포넌트 리렌더링 > 자식 컴포넌트 리렌더링
  - 얕은 비교 > 새로운 값 파악 > 새로운 값인 경우에만 `리렌더링`
- 얕은 비교 (참조타입)
  - 실제 내부 값 비교 아닌 > 동일 참조(동일한 메모리 값 사용 여부)

### 리엑트 불변성 > `상태업데이트` `사이드 이펙트 방지` 2가지 이점!
> [참고자료](https://hsp0418.tistory.com/171)
- 리엑트 상태 업데이트 원리 떄문에 사용
- 불변성 이점 > 사이드 이펙트 방지!
  - 외부 존재하는 원본데이터 직접 수정 x
  - 원본데이터의 복사본 사용하지 않아 사전 오류 방지!
- 자바스크립트 메모리 구조 [참고자료](https://lasbe.tistory.com/143)
  - ![image](https://github.com/hyunolike/info-docs/assets/61215550/54c3590c-ea99-4320-b95b-4f3a51595d33)
  - 원시 타입: Boolean, String, Number, null, undefined, Symbol
  - 참조 타입: Object, Array, Function ⭐
### 사용 예시
```js
dialog: (options) => { 
    set(
      produce<DialogStoreType>((state) => {
        state.open = true;
        state.state = { ...state.state, ...options };
      })
    );
    return new Promise<void>((resolve, reject) => {
      set(
        produce<DialogStoreType>((state) => {
          state.awaitingPromise = { resolve, reject };
        })
      );
    });
  },
```
