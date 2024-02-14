## 숫자 천단위 처리
> [참고자료](https://computer-science-student.tistory.com/718)
### `toLocaleString()`
```js
let num = 123456789;
console.log(num.toLocaleString()); // 123,456,789

// 잘못된 사용예시
let strNum = "123456789";
console.log(strNum.toLocaleString()); // 123456789
```
