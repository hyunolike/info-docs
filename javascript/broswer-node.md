## 브라우저 환경 부모, 자식, 형제 찾기 & 선택
> [참고자료](https://itun.tistory.com/501) <br/>
> [MDN](https://developer.mozilla.org/ko/docs/Web/API/Element/children)

### childNodes
```js
// 엄마 생성
var mother = document.getElementById('mother'); ⭐ ID 값 !!!
// 모든 자식 찾기
var every = mother.childNodes;
// 첫번째 자식새끼 찾기
var one = mother.firstChild;
// 세번째 아들내미 찾기
var three = mother.lastChild;
```

### parentNode
```js
var one = document.getElementById('one');
var mother = one.parentNode;

⭐ 부모의 부모 찾을래
var one = document.getElementById('one');
var grandparents = one.parentNode.parentNode;
```

### children
- 자식 요소 가져온다
#### 사용예시.
```js
let a = document.getElementById('popupNotice');
let aCnt = popupNotice.childElementCount;

if (aCnt > 0) {
    let lis = popupNotice.children;

    for (let i = 0; i < lis.length; i++) {
        let childNode = lis[i];
        let id = childNode.id;

        if (id) {
            console.log(id);
        }
    }
```



