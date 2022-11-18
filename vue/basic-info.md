## Vue.js 
> [참고자료](https://joshua1988.github.io/web-development/vuejs/vuejs-tutorial-for-beginner/)
### 1. 개념잡기
- ✔ `MVVM` 패턴의 **ViewModel** 레이어에 해당하는 화면단 라이브러리
  - 간단하게! DB 데이터 처리 및 서버 로직 + 뒷단에서 넘어온 데이터 Model에 담아 View 넘겨주기 >> `중간 지점`
- ![image](https://user-images.githubusercontent.com/61215550/202589713-6cc05f4a-9bc1-494a-80c3-5a92715f49b0.png)
  - 데이터 바인딩, 화면 단위를 컴포넌트  형태로 제공, 관련 API 지원 >> 목적 ⭐
  - Angular에서 지원하는 **양방향 데이터 바인딩** 제공
  - 컴포넌트 간 통신의 기본 골격 >> React의 단방향 데이터 흐름(부모 > 자식) 사용
  - 다른 프레임웍에 비해 상대적 가볍고 빠름
  - 문법 단순하고 간결하여 초기 학습 비용이 낮고 누구나 쉽게 접근 가능

### 2. Vue Instance 😛
- 화면 개발하기 위한 필수 단위!
- 생성 방법


```javascript
new Vue({
  template: "",
  el: "",
  method: {}
  // ..
})
```

#### 2-1. Vue Instance 라이프싸이클 초기화
- 초기화 작업 4가지
  - 데이터 관찰
  - 템플릿 컴파일  
  - DOM 객체 연결
  - 데이터 변경시 DOM 업데이트

### 3. Vue Components
- 화면 영역을 일정한 단위로 쪼개어 재활용 가능한 형태로 관리하는 것! >> 컴포넌트


```html
<div id="app">
  <my-component></my-component>
</div>
```


```javascript
new Vue({
  el: "#app",
  
  component: {
    "my-component":{
      template: "<div>A custom component! </div>"
    }
  }
})
```

#### 3-1. Global or Local Component
##### ✔전역 컴포넌트 등록 방식
```javascript 
Vue.component('my-component', {
  template: '',
})
```
##### ✔지역 컴포넌트 등록 방식
```javascript
var cmp = {
  template: '',
  ...
}

new Vue({
  components: {
    'my-cmp': cmp
  }
})
```

### 4. 부모와 자식 컴포넌트 관계
> ⭐ 주의할점: `props` 변수 명을 카멜 기법으로 정의하면 html 태그에서 사용할 때는 `케밥 기법(-)` 으로 선언!
- 위에서 아래 `데이터(props)` 내리기
- 아래에서 위 `이벤트(event emit)` 올리기
- ![image](https://user-images.githubusercontent.com/61215550/202590983-7eb75c24-35c1-474c-8b13-f5a7daaef9f6.png)

#### 4-1. 같은 레벨의 컴포넌트 간 통신
- Child(하위) -> Parent(상위) -> Child(하위 2개)
- ✔ 컴포넌트 간의 직접적인 통신은 불가능! 뷰의 기본 구조

#### 4-2. Event Bus
- 상위-하위 관계 x >> 컴포넌트 간의 통신을 위해 사용!
##### 1. 이벤트 사용하기 위한 새로운 뷰 생성
```javascript
var eventBus = new Vue();

new Vue({
  ...
})
```

##### 2. 이벤트 ⚡발생시킬 컴포넌트 `$emit()` **호출**
```javascript
eventBus.$emit("refresh", 10);
```

##### 3. 이벤트 👨‍💻받을 컴포넌트에서 `$on()` 이벤트 **수신**
```javascript
new Vue({
  created: function() {
    eventBus.$on("refresh", function(data) {
      console.log(data);
    });
  }
})
```
##### 4. `eventBus` 콜백 함수안에서 해당 컴포넌트의 메서드 참고하기 위해 `vm` 사용
```javascript
new Vue({
  methods: {
    callAnyMethod() {
      ...
    }
  },
  created() {
    var vm = this;
    eventBus.$on("refreash", function(data) {
      console.log(this);
      vm.callAnyMethod();
    });
  }
})
```

### 5. Vue Routers
- SPA 제작할 때 유용한 라우팅 라이브러리!
#### 5-1. Nested Routers
- **지정된 하위** 컴포넌트를 표시!
- 컴포넌트 구조: 큰 상위의 컴포넌트가 하위 컴포넌트 포함하는 `부모-자식` 관계



```html
<!-- localhost:5000 -->
<div id="app">
</div>

<!-- localhost:5000/home -->
<div>
  <p>Main Component rendered</p>
  <app-header></app-header>
</div>

<!-- localhost:5000/list -->
<div>
  <p>List Component rendered</p>
  <List></List>
</div>
```


```javascript
{
  path: '/home',
  component: Main,
  children: [
    {
      path:'/',
      component: AppHeader
    },
    {
      path: '/list',
      component: List
    },
  ]
}
```
#### 5-2 Named Views
- 특정 url로 이동했을 때 여러 개의 컴포넌트를 **동시에 표시할** 수 있는 방법
```html
<div id="app">
  <router-view name="appHeader"></router-view>
  <router-view></router-view>
  <router-view name="appFooter"></router-view>
</div>
```



```javascript
{
  path : '/home',
  // Named Router
  components: {
    appHeader: AppHeader,
    default: Body,
    appFooter: AppFooter
  }
},
```
#### 5-3. 비교
![image](https://user-images.githubusercontent.com/61215550/202593814-d14da5da-7f36-40a9-a55a-4664e5de6720.png)

### 6. Vue Template
- 뷰로 화면 조작하기 위해 제공되는 문법
- 2가지 
  - 뷰 인스턴스에서 관리하는 데이터를 화면에 연결하는 **데이터 바인딩**
  - 화면 조작을 편하게 하는 **디렉티브**

#### 6-1. Data Binding
- `{{}}` 콧수염 문법
  - data, computed, props 속성 연결

#### 6-2. Directive
- html 태그 속성 `-v` 접두사가 붙은 특별한 속성


```html
<!-- seen의 진위 값에 따라 p 태그가 화면에 표시 또는 미표시 -->
<p v-if="seen">Now you see me</p>
<!-- 화면에 a 태그를 표시하는 시점에 뷰 인스턴스의 url 값을 href에 대입 -->
<a v-bind:href="url"></a>
<!-- 버튼에 클릭 이벤트가 발생했을 때 doSomething이라는 메서드를 실행 -->
<button v-on:click="doSomething"></button>
```
#### 6-3. Filters
- 화면에 표시되는 텍스트 형식 편하게 바꿀 수 있도록 고안되 기능
- `|` 사용


```html
<!-- message 값에 capitalize 필터를 적용하여 첫 글자를 대문자로 변경 -->
{{ message | capitalize }}
```


### 7. Single File Component
- 특정 화면 `html` `css` `js` 코드 한파일에서 관리할 수 있는 방법


```
<template>
  <!-- HTML -->
</template>

<script>
  // Javascript
</script>

<style>
  /* CSS */
</style>
```
### 8. Vue Loader 
- 싱글 파일 컴포넌트를 브라우저에서 실행할 수 있게 자바스크립트 파일로 변환해주는 웹팩 로더. 

### 9. Vue CLI
- 뷰 프로젝트 생성하기 위한 명령어 도구

### 10. Virtual DOM in Vue.js
