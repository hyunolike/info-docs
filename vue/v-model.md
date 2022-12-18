## `v-model` 동작 원리 / 활용 방법
> [참고자료](https://joshua1988.github.io/web-development/vuejs/v-model-usage/)
- ✔ 입력 받는 ui 요소들에 해당 속성 사용 시 >> 입력 값이 자동으로 **뷰 데이터 속성과 연결**


```js
<input v-model="inputText"> 

new Vue({
  data: {
    inputText: ''
  }
})
```


- ![image](https://user-images.githubusercontent.com/61215550/208326100-62bff848-68ba-4091-98c0-4757f5a000eb.png)

### 동작 원리
- `v-model` = `v-bind` + `v-on` 
  - `v-bind`: 뷰 인스턴스의 데이터 속성 HTML 요소 연결할 때 사용
  - `v-on`: 해당 HTML 요소의 이벤트를 뷰 인스턴스의 로직과 연결할 때 사용

### 한계점 ㅠ,ㅠ
> 한국어 입력 다룰 때 >> `v-bind:value` `v-on:input` 직접 연결하는 것을 권고
- 😛빠르게 구현 및 프로토타이핑 좋아
- 🙄 현시점 IME 입력에 대해 반응이 느려 ...


### `v-model` 문법 이용 >> 한국어 처리는? 
- 별도의 컴포넌트로 분리!!


```js
<template>
  <div>
    <base-input v-model="inputText"></base-input>
  </div>
</template>

<script>
import BaseInput from './BaseInput.vue';

export default {
  components: {
    'base-input': BaseInput
  },
  data: function() {
    return (
      inputText: ''
    )
  }
}
</script>
```
