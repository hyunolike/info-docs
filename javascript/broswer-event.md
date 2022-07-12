## 브라우저 이벤트
### 1. 이벤트 핸들러
- 이벤트 발생했을 때 실행할 함수 >> 핸들러
#### 1.1 HTML 속성
- HTML 안 `on<event>`
- `<input value = "..." onclick = "alert('클릭')" type="button" />`
- ✔ 속성값은 대개 __소문자__ 로 작성

#### 1.2 DOM 프로퍼티
```javascript
<input type="button" id="elem" onclick="alert('이전')" value="클릭해 주세요."> 
<script>
  elem.onclick = function() { // 기존에 작성된 핸들러를 덮어씀
    alert('이후'); // 이 경고창만 보입니다.
  };
</script>
```

#### 1.3 this로 요소 접 
- `<button onclick="alert(this.innerHTML)">클릭해 주세요.</button>`

#### 1.4 자주하는 실수
- `sayThanks` 로 할당 >> `sayThanks()` 할당 시 동작 안함
```javascript
// 올바른 방법
button.onclick = sayThanks;

// 틀린 방법
button.onclick = sayThanks();
```
#### 1.5 `addEventListener` `removeEventListener`
- `element.addEventListener(event, handler, [option]);`
  - `event` 이벤트 이름
  - `handler` 핸들러 함수
  - `option` 아래 프로퍼티를 갖는 객체

#### 1.6 이벤트 객체
- 이벤트 발생 시 상세 내용 파악 가능
  - `event.type`
  - `eventcurrentTarget`
  - `event.clientX / event.clientY`

#### 1.7 객체 형태의 핸들러와 handleEvent
- ...

### 2. 요약
1. HTML 속성
2. DOM 프로퍼티
3. 메서드
