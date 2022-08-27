## React + Typescript
- ⭐️ 타입스크립트: 자바스크립트의 일부분 업그레이드해서 사용하고 싶을 때 설치해서 쓰는 일종의 자바스크립트 대용품!
  - 즉, 완전 다른 언어가 아닌 자바스크립트 문법 그대로 이용가능 >> 타입문법을 업그레이드해서 사용 가능
  - 이유, 자바스크립트는 타입에 관대! >> 아무런 제지가 없다(지가 알아서 타입 변경 해줌) 
  - 하지만, 타입스크립트는 이런걸 전부 에러로 잡아줌 >> 타입 관련해서 에러 잡아주니까 타입스크립트?
- 설치 `npm i -g typescript`
- 브라우저는 타입스크립트 인식못함 >> js 파일 변환 필요!

### React 에서 사용하기
#### 1. 이미 있는 React 프로젝트에 설치
- `npm install --save typescript @types/node @types/react @types/react-dom @types/jest

#### 2. 새로 만드는 거면
- `npm create-react-app my-app --template typescirpt`

### 타입스크립트 문법 간단하게
```typescript
let 이름 :string = 'jang';
// 타입 종류: string, number, boolean, bigint, null, undefined, [], {}

let 이름: string[] = ['jang', 'park'];
let 이름: { age : number } = { age : number };

// 여러가지 변수
let 이름 :string | number = 'jang';

// 타입에 직접 넣을수도 있어
type nameType = string | number;
let 이름 :nameType = 'jang';

// 타입에 나만의 타입을 만들수도 있어 >> literal type 이라고 불려
type NameType = 'jang' | 'hyunho'
let 이름 :NameType = 'jang';
```
