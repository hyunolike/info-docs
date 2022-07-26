## `require` vs `import`
> [참고자료](https://inpa.tistory.com/entry/NODE-%F0%9F%93%9A-require-%E2%9A%94%EF%B8%8F-import-CommonJs%EC%99%80-ES6-%EC%B0%A8%EC%9D%B4-1)

- ✔ require: `NodeJS`에서 사용되고 있는 CommonJS 키워드
- ✔ import: ES6(ES2015)에서 새롭게 도입된 키워드
- 모두 다른 파일의 코드를 불러온다는 동일한 목적


```javascript
const moment = require("moment"); // CommonJS 방식
import moment from "moment"; // ES6 방식
```

- `CommonJS` 방식: 다른 변수를 할당하듯이 모듈 불러옴
- `ES6` 방식: Java, Python 처럼 import 키워드 사용해 좀 더 명시적으로 모듈 불러옴

### 주요 차이점
|`require()`|`import`|
|-----------|-----------|
|node.js문|ES6|
|파일이 들어있는 곳에 남아있음|항상 맨위|
|프로그램의 어느 지점에서 호출 가능|파일 시작 부분에서 실행 가능 <br> import 전용 비동기 문법으로 처리 가능|
|프로그램에서 동시 사용할 수 없음|프로그램에서 동시 사용할 수 없음|
||- 필요한 모듈 부분만 선택 가능 <br>- require()보다 성능 좋음|

### 모듈 `export`
- ES6


```javascript
// 모듈 전체를 export, 파일내 한번만 사용가능하다.
var module = {};
export default module
 
 
// 모든 속성을 export
export *;
 
 
// 함수를 직접 export
export function moduleFunc() {};
var property = "some property";
export {property};
```
- CommonJS
```javascript
// 모듈 전체를 export
module.exports = module
 
// 함수를 직접 export
exports.moduleFunc = function() {}
```

### 모듈 import
- ES6


```javascript
import module
import module as myModule
 
 
// 모든 속성 import
import * as name from module
 
 
// 특정 멤버(함수 등)만 import
import {moduleFunc, moduleFunc2} from module
```
- CommonJS


```javascript
// 모듈 전체를 import
var module = require('./someModule.js')
 
 
// 특정 멤버(함수 등)만 import, 위의 module을 이용한다.
module.moduleFunc1
module.moduleFunc2
 
 
// 특정 멤버(함수 등)만 import
var {moduleFunc, moduleFunc2} from require('./someModule.js')
```
