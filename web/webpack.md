## webpack
> [참고자료](https://joshua1988.github.io/webpack-guide/concepts/overview.html#%EC%9B%B9%ED%8C%A9%EC%9D%98-4%EA%B0%80%EC%A7%80-%EC%A3%BC%EC%9A%94-%EC%86%8D%EC%84%B1)

### 4가지 주요 속성 - `concept`
- entry
- output
- loader
- plugin

#### ✅ entry
- 웹 자원 변환하기 위해 필요한 **최초 진입점** 
- SPA (아래는 dependency graph)
  - ![image](https://user-images.githubusercontent.com/61215550/211183315-ea3f1619-e234-4691-91a5-ab1c9ca06e92.png)
- 유형 여러가지 가능!

#### ✅ output
- 웹팩을 돌리고 난 후 결과물의 파일 경로!


```js
// webpack.config.js
module.exports = {
  output: {
    filename: 'bundle.js'
  }
}
```
#### ✅ loader
- 웹팩 >> 웹 애플리케이션 해석 >> 자바스크립트 파일이 아닌 웹자원들을 변환할 수 있도록 도와주는 속성


```js
// webpack.config.js
module.exports = {
  module: {
    rules: []
  }
}
```


- 😛 로더 적용 순서 `오른쪽부터 왼쪽`
#### ✅ plugin
- 기본적인 동작 + `추가적인 기능` 
- 로더와 비교
  - 로더: 파일 해석, 변환하는 과정
  - 플러그인: 해당 결과물의 형태를 바꿈
- <img width="626" alt="image" src="https://user-images.githubusercontent.com/61215550/211183490-a7f8e9b8-1dae-4350-bc65-c515220a6c49.png">
  
