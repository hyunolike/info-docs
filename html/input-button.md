## `input` `button` 공통점&차이점
> [참고자료](https://cocoder16.tistory.com/18)

### button 태그 하는 일
- 기본 동작 > `form` **submit** 👨‍🌾
- type 기본값 >> `submit`
### button type 속성
- `submit` 폼 제출하는 이벤트 활성화
- `reset` 폼안에 작성된 내용 초기화
- `button` 그 자체로 아무런 이벤트 동작 없음 / click 이벤트 연결해 자바스크립트 활용하는 방법 다수 사용!

### 🔥 `input` vs `button` 
#### 1. 차이점
- button  스스로 닫지 않는 태그
  - 하위 태그 추가 가능
- input 스스로 닫는 태그


```html
<input type="button" />
<button type="button">
  <img src="http://res.publicdomainfiles.com/pdf_view/89/13942613416804.png" alt="arrow">
</button>

<!-- css -->
input {
  width: 200px; height: 200px;
  background-image: url(http://res.publicdomainfiles.com/pdf_view/89/13942613416804.png);
  background-size: 100% 100%;
}
button {
  width: 200px; height: 200px;
}
img {
  width: 100%; height: 100%;
}
```
