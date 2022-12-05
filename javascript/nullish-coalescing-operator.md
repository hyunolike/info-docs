## 널 병합 연산자
> [참고자료](https://joshua1988.github.io/vue-camp/es6+/nullish-coalescing-operator.html#%E1%84%80%E1%85%B5%E1%84%8C%E1%85%A9%E1%86%AB-%E1%84%86%E1%85%AE%E1%86%AB%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%A7%E1%86%AF-%E1%84%92%E1%85%A1%E1%86%AF%E1%84%83%E1%85%A1%E1%86%BC-%E1%84%87%E1%85%A1%E1%86%BC%E1%84%89%E1%85%B5%E1%86%A8)
- ✔ `??` 왼쪽의 피연산자 null, undefined 일때 오른쪽 피연산자 반환! 아니면 왼쪽 꺼


```javascript
function printTitle(text) {
  let title = text ?? 'Cracking Vue.js';
  console.log(title);
}

printTitle('Crack'); // Crack
printTitle(); // Cracking Vue.js
```
