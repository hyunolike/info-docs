## Type Alias vs Interface
> ✔보통 `interface` 사용!
```javascript
interface Human {
  name: string;
  age: number;
}

const henry: Human = {
  name: '남현욱',
  age: 20,
};

//

type Human = {
  name: string;
  age: number;
};

const henry: Human = {
  name: '남현욱',
  age: 20,
};
```

### 1. 차이점
#### 1.1 `Interface` 선언 통합
- 동일한 이름으로 여러 번 선언해도 컴파일 시점에 아래처럼 합칠수 있음 


```javascript
interface Window {
  title: string;
}

interface Window {
  ts: import("typescript");
}

declare function getWindow(): Window;

const window = getWindow();
const src = 'const a = "Hello World"';
window.ts.transpileModule(src, {});    // transpileModule() 메서드 사용 가능
```
