## `emotion` `styled-components`
> [참고자료](https://velog.io/@bepyan/styled-components-%EA%B3%BC-emotion-%EB%8F%84%EB%8C%80%EC%B2%B4-%EC%B0%A8%EC%9D%B4%EA%B0%80-%EB%AD%94%EA%B0%80)
- react > `css-in-JS` 주로 사용
- 위 2개 모두 `scss` 문법 사용하기 문제 없음

### 1. 용량, 성능
- 성능상 유의미하게 차이 나지 않음

### 2. emotion 차이
#### 2-1. `css props` 
```js
<div css={[style, themes[theme], sizes[size]]} />
  
const themes = {
  primary: css`
    color: red;
  `,  
  secondary: css`
    color: blue;
  `
}
const sizes = {
  small: css`
    fontSize: 0.75rem;
  `,
  medium: css`
    fontSize: 1rem;
  `
}
```
#### 2-2. SSR
- SSR > 별도의 설정 없이 동작 가능
- sytled-components 같은 경우 `ServerStyleSheet` 설정 필요
