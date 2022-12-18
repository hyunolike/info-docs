## 타입스크립트
### 1. 자바스크립 단점 - 개발자를 도와주지 않아!!
- 자바스크립트는 말도 안되는 행위도 다 허용해줘!! 🥺
  - `[1, 2, 3, 4] + false` >> `"1,2,3,4false"` 다른언어였으면 에러 나왔을꺼야
- 자바스크립트는 에러를 안보여주고 그냥 실행시켜줌 ㅠ,ㅠ >> 보호 못받아
- 코드 실행전에 에러를 안알려줘

### 2. 타입스크립트 - 개발자의 멍청한 짓 막아줌!!
> [참고자료](https://www.typescriptlang.org/play)
- 작성한 코드가 자바스크립트로 변환 
  - 😃 변환하는 이유: `브라우저` 는 자바스크립트 이해(인식) / `Node.js` 는 타입스크립트 & 자바스크립 이해 가능!
- 타입스크립트가 에러가 발생할거 같으면 자바스크립트로 변환을 안해줘

#### 2-1. 타입추론
- 미리 에러를 알려줌!! 실행전에
- Implicit Types, Explicit Types
- optional Types 


```typescript
let o : {
  name : string,
  age ?: number
} = {
  name : 'hyunho'
  }
```


- 별칭 타입 (타입 재사용)


```typescript
type Player = {
  name : string,
  age ?: number
}

let o : Player = {
  name : 'hyunho'
}
```


