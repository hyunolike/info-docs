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
