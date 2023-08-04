## 스크롤바 스타일 적용
> [참고자료](https://codingbroker.tistory.com/66)
- ⭐ 스크롤바 스타일 웹표준 존재 x
  - `webkit` 브라우저(크롬, 사파리, 오페라) 한해서 가상요소 사용 > 스타일 적용 가능
### 스크롤바 가상요소 3가지(크롬 기준)
- `::-webkit-scrollbar`: 스크롤바 전체
- `::-webkit-scrollbar-thumb`: 스크롤 막대
- `::-webkit-scrollbar-track`: 스크롤 막대 외부
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/819cba6a-5d39-4d57-8d67-d15aa836ef9d)
### 예시
```css
  .container {
    width: 250px;
    height: 140px;
    overflow: auto;
  }
  .container::-webkit-scrollbar {
    width: 10px;
  }
  .container::-webkit-scrollbar-thumb {
    background-color: #2f3542;
    border-radius: 10px;
  }
  .container::-webkit-scrollbar-track {
    background-color: grey;
    border-radius: 10px;
    box-shadow: inset 0px 0px 5px white;
```
