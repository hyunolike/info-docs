## Webpack Dev Server
> [참고자료](https://joshua1988.github.io/webpack-guide/devtools/webpack-dev-server.html#webpack-dev-server)
- 개발하는 과정 >> 유용한 도구
- 코드만 변경하고 저장하면 웹팩으로 빌드 후 >> 브라우저 새로고침!

### 특징
- webpack dev server로 빌드한 결과물 >> 메모리 저장 / 파일 생성 안함!
- 컴퓨터 내부적으로만 접근 가능
- ⭐컴퓨터 구조 관점 >> 파일 입출력보다 메모리 입출력이 더 빠르고 컴퓨터 자원 덜 소모

### 프록시 설정 ✔
```js
module.exports = {
  devServer: {
    proxy: {
      '/api': 'http://localhost:3000'
    }
  }
}
```


- ![image](https://user-images.githubusercontent.com/61215550/207739588-666fbb0c-de3c-45f0-8432-693ff8403666.png)
#### CQRS 
> 브라우저 보안
- 😛 다른 도메인 간에는 자바스크립트 자원 요청할 수 없다는 의미! (아래 코드처럼 설정)


```js
module.exports = {
  devServer: {
    proxy: {
      '/api': {
        target: 'domain.com',
        changeOrigin: true
      }
  }
}
```


- ![image](https://user-images.githubusercontent.com/61215550/207739719-00a3afce-0d93-455c-b34b-2d8a2a1555f5.png)
