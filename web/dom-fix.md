## 문서 수정
> [참고자료](https://ko.javascript.info/modifying-document)

### 1. 요소 생성
- `document.createElement(tag)`: tag 사용 >> 새로운 요소 만듦
- `document.createTextNode(text)`: text 사용 >> 텍스트 노드 만듦 

### 2. 삽입 메서드
> 생성한 요소를 보여줘야되!
- `document.body.append(div)`


|메서드|설명|
|----|----|
|`node.append(노드나 문자열)`|노드나 문자열 `node` 끝에 삽입|
|`node.prepend(노드나 문자열)`|노드나 문자열 `node` 맨 앞에 삽입|
|`node.before(노드나 문자열)`|노드나 문자열 `node` 이전에 삽입|
|`node.after(노드나 문자열)`|노드나 문자열 `node` 다음에 삽입|
|`node.replaceWith(노드나 문자열)`|`node`를 새로운 노드나 문자열로 대체|


- ![image](https://user-images.githubusercontent.com/61215550/211974678-d0f38d4a-b8bf-4a31-a24b-7e28918944ea.png)

### 3. insertAdjacentHTML/Text/Element
- `elem.insertAdjacentHTML(where, html)`
- ![image](https://user-images.githubusercontent.com/61215550/211974843-d1262228-e69b-4887-8a53-2437ba9ded99.png)

### 4. 노드 삭제
- `node.remove()`

### 5. 노드 복제, `cloneNode`

---
![image](https://user-images.githubusercontent.com/61215550/211975120-761dd835-bfaa-437c-b67f-2ad5f0debc8d.png)
