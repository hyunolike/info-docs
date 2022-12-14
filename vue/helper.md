## `Vuex` `Helper`
- Store에 있는 아래 4가지 속성들을 **간편하게 코딩하는 방법**
  - state > `mapState`
  - getters > `mapGetters`
  - mutations > `ampMutations`
  - actions > `mapActions`

### 1. mapState
- Vuex에 선언한 state 속성을 뷰 컴포넌트에 더 쉽게 연결해주는 헬퍼

### 2. mapGetters
- Vuex에 선언한 getters 속성을 뷰 컴포넌트에 더 쉽게 연결해주는 헬퍼

### 3. mapMutations
- Vuex에 선언한 mutations 속성을 뷰 컴포넌트에 더 쉽게 연결해주는 헬퍼

### 4. mapActions
- ...Actoins 속성 ... 쉽게 ... 헬퍼 ㅋㅋㅋㅋㅋ

### 5. 헬퍼의 유연한 문법
#### 5-1. 배열 리터럴 - Vuex 선언한 속성 **그대로 컴포넌트에 연결하는** 문법
```js
...mapMutations([
  'clickBtn',
  'addNumber'
])
```
#### 5-2. 객체 리터럴 - Vuex 선언한 속성 >> **컴포넌트의 특정 메소드** 연결하는 문법
```js
...mapMutations({
  popupMsg: 'clickBtn'
})
