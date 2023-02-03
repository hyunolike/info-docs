## 서버나 디비 없이 프론트로만 데이터 저장하는 방법 - `local storage` - `UPDATED BY 2023/02/03` 
![image](https://user-images.githubusercontent.com/61215550/202375501-176d3752-7b1c-429c-a34b-4beda9fc6497.png)

## (추가) localStorage & sessionStorage
> [참고자료](https://ko.javascript.info/localstorage)
- 둘다 웹 스토리지 객체
  - `sessionStorage`: 페이지 새로 고침해도 남아있어
  - `localStorage`: 브라우저 다시 실행해도 남아있어
- 모두 서버가 아닌 자바스크립트 내에서 객체조작 가능!!

### 1. `localStorage` 주요 기능
- 😛 `오리진` 같은 경우 데이터는 모든 탭과 창에서 공유
  - 오리진? `domain/port/protocol` !! URL 경로 달라도 동일한 결과 볼 수 있음!
- 브라우저 / OS >> 재시작해도 데이터 파기 x


|함수|설명| 
|---|----|
|`setItem(key, value)`|키 값 쌍 보관|
|`getItem(key)`|키에 해당하는 값 받기|
|`removeItem(key)`|키와 해당 값 삭제|
|`clear()`|모든 것 삭제|
|`key(index)`|인덱스에 해당하는 키 받기|
|`length`|저장된 항목의 개수 얻기|

#### 1-1. 작성 시, 자동으로 로컬스토리지 저장되는 로직! 🍻
```js
<!doctype html>
<textarea style="width:200px; height: 60px;" id="area" placeholder="Write here"></textarea>
<br>
<button onclick="localStorage.removeItem('area');area.value=''">Clear</button>
<script>
    area.value = localStorage.getItem('area');
    area.oninput = () => {
      localStorage.setItem('area', area.value)
    };
</script>
```


### 2. `sessionStorage`
- 자주 사용되지 않아!!!!!!!
- 현대 떠 있는 탭 내에서만 유지
  - 같은 페이지라도 다른 탭에 있으면 다른 곳에 저장
- 페이지 새로 고침해도 데이터 사라지지 않음! 탭을 닫고 열때 사라짐

### ✔요약
- 키, 값 반드시 문자열
- 제한 용량 5MB >> 브라우저 따라 달라짐
- 파기되지 않음
- 오리지(도메인.포트.프로토콜) 묶여있음
---
## (추가) ⭐브라우저에 데이터 자장하기
- 쿠키 & document.cookie
- localStorage & sessionStorage
- IndexDB
