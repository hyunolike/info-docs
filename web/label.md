## label 태그
> [참고자료](https://abcdqbbq.tistory.com/63)
- ⭐ 양식 입력 창의 요소들을 위한 캡션!
- 코드 작성 방식 >> 명시적 / 암시적
- ✔ 쓰는 이유 >> **웹 접근성!!** - [참고자료](https://ninetynine-2026.tistory.com/551)

### 명시적
```html
<label for="age">나이</label>
<input type="number" id="age">
```
### 암시적
```html
<label>
   <input type="number" id="age">
</label>
```
