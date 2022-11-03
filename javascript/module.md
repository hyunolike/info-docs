## `module.export` `export default` 차이!!!? 궁금
> [참고자료](https://dev-deskch.tistory.com/14)

- ✔ `import` `export` ES6에서 공식적으로 채택된 **모듈화 방식**

### 1. `default` 
- 기본값으로 내보낼 함수, 객체 
- 받아올때는 `import` !! ⭐
- 사용자가 원하는 대로 이름 지정 가능


```javascript
// export.js
const a = 1;
const b = 2;

export { a };
export const c = 3;
export default b;

----------------------

// import.js
import d, { a, c as e } from 'export';
console.log(d, a, e); // 2, 1, 3
```

### 2. `module`
- Node.js와 이전의 브라우저 >> `commonJS` 기반의 require 키워드 이용해 모듈화 시킴!
- module 객체에 담아 내보낸다고 생각하면 좋음~~


```javascript
// export.js
const a = 'a';
const b = 'b';

module.exports = { a, b }

----------------------

// import.js
const alphabet = require('export');

console.log(alphabet); // { a: 'a', b: 'b' }
```
