## 브라우저 이벤트 `업데이트` + 이벤트 객체
> [참고자료](https://inpa.tistory.com/entry/JS-%F0%9F%93%9A-%EC%9D%B4%EB%B2%A4%ED%8A%B8-%F0%9F%92%AF-%EC%B4%9D-%EC%A0%95%EB%A6%AC)
### 1. 브라우저 이벤트
- 사용자 상호작용
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/403eaad2-23ee-492b-aef4-a7cd02c7ca12)
### 2. ⭐이벤트 등록 방법
- 3가지
  - `inline` 방식
  - 프로퍼티 방식
  - `addEventListner` 방식   
### 3. ⭐이벤트 핸들러 내부 `this` 이용
```js
<button onclick="foo()">Button</button>

<script>
    function foo () {
      console.log(this); // window
    }
</script>
```
### 4. ⭐⭐이벤트 객체
- 이벤트 발생시킨 요소
- 이벤트에 대한 유용한 정보
- 이벤트 발생!
  - 이벤트 객체 동적 생성
  - 이벤트 처리 가능 > 이벤트 핸들러 인자로 전달! ✔
#### 4-1. 이벤트 객체 종류
- `Event.target`
  - 이벤트 발생시킨 요소 > 버블링 주의
- `Event.currentTarget`
  - `addEventListener` 앞에 기술된 객체
  - `currentTarget` ==  `this`
 

## 브라우저 이벤트
> [참고자료](https://ko.javascript.info/introduction-browser-events) <br/>
> ✔ 핸들러 3가지: `onclick=...` `elem.onclick = function` `elem.addEventListner(event, handler[,phase])`
- 마우스 이벤트
- 폼 요소 이벤트
- 키보드 이벤트
- 문서 이벤트
- CSS 이벤트

### 1. 이벤트 핸들러
- 이벤트 발생 시 실행하는 함수 `handler`
  - 사용자의 행동 >> 자바스크립트 코드로 표현
#### 1-1. HTML 속성
```html
<input value="클릭해 주세요." onclick="alert('클릭!')" type="button">
```


- html 속성 대소문자 구분 ❌
- 일반적으로 `onclick` 같이 소문자로 작성!
#### 1-2. DOM 프로퍼티
```html
<input id="elem" type="button" value="클릭해 주세요.">
<script>
  elem.onclick = function() {
    alert('감사합니다.');
  };
</script>
```

#### 1-3. addEventListner
- 핸들러 여러 개 할당 가능!


```js
element.addEventListener(event, handler, [options]);
```
