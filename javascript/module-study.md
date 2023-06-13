## 모듈
> [참고자료](https://ko.javascript.info/modules-intro)
- 분리된 파일 = 모듈
  - 클래스, 특정한 목적 가진 복수의 함수, 라이브러리
- 모듈 가져오는 방식 2가지
  - 정적인 방식
  - 동적인 방식
### 1. 모듈 시스템 
> 3가지
- `AMD`: 가장 오래도니 모듈 `require.js` 라이브러리 통해 처음 개발
- `CommonJS`: `Node.js` 서버 위해 만들어진 모듈 시스템
- `UMD`: AMD / CommonJS 와 같은 다양한 모듈 시스템 함께 사용하기 위해 만들어짐
### 2. 모듈
- 단지 하나의 파일
  - 스크립트 하나
- `export`: 외부 모듈에서 해당 변수나 함수 접근 가능 ⭐모듈 내보내기
- `import`: 외부 모듈의 기능 가져올 수 있음 ⭐모듈 가져오기
#### ✔ 모듈은 로컬 동작 x >> `HTTP` `HTTPS` 프로토콜 통해 동작!!
### 3. 모듈 핵심 기능
- 엄격 모드로 실행
- 모듈 레벨 스코프
- 단 한 번만 평가 >> 모듈은 최초 호출 시 단 한번만 실행!
### 4. 브라우저의 특정 기능 `type="module"`
- 지연 실행
- 인라인 스크립트의 비동기 처리
- 외부 스크립트
- 경로가 없는 모듈은 금지
- 호환을 위한 nomodule
### 5. 빌드 툴
- 브라우저 환경 >> 모듈 단독 사용 경우 흔치 않음
- 웹팩 >> 모듈 묶어(번들링) 프로덕션 서버 올리는 방식
---
## 모듈 사용
> [참고자료](https://ko.javascript.info/import-export)
1. 선언부 앞에 `export` 붙이기
2. 선언부와 떨어진 곳에 export 붙이기
3. `import *`
4. `import as`
5. `export as`
6. `export defualt`


```javascript
// 배열 내보내기
export let months = ['Jan', 'Feb', 'Mar','Apr', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];

// 상수 내보내기
export const MODULES_BECAME_STANDARD_YEAR = 2015;

// 클래스 내보내기
export class User {
  constructor(name) {
    this.name = name;
  }
}
```
### 1. 모듈 종류 `export default` >> 개체가 하나만 존재!! 해당 모듈은 !!!
> 크게 2가지
- 복수의 함수 있는 `라이브러리` 형태 
- 개체 하나만 선언되어 있는 모듈 ✔ 선호 방식!! `export default`

## 😛 동적으로 모듈 가져오기
> [참고자료](https://ko.javascript.info/modules-dynamic-imports)
```javascript
// 📁 say.js
export function hi() {
  alert(`안녕하세요.`);
}

export function bye() {
  alert(`안녕히 가세요.`);
}
---
let {hi, bye} = await import('./say.js');

hi();
bye();
```
