## `axios` `fetch`
> [참고자료](https://velog.io/@shin6403/React-axios%EB%9E%80-feat.-Fetch-API)
- 리엑트 >> ui library
  - http client 내장된 angular와 달리 리엑트는 내장 클래스 따로 없음
  - ajax 구현 시 >> 내장객체 `XMLRequest` `HTTP Client` 사용해야 됨 ㅠ.ㅠ

### fetch
```javascript
//fetch
const url ='http://localhost3000/test`
const option ={
   method:'POST',
   header:{
     'Accept':'application/json',
     'Content-Type':'application/json';charset=UTP-8'
  },
  body:JSON.stringify({
  	name:'sewon',
    	age:20
  })

  fetch(url,options)
  	.then(response => console.log(response))
```

### axios
```javascript
//axios
const option ={
  url ='http://localhost3000/test`
   method:'POST',
   header:{
     'Accept':'application/json',
     'Content-Type':'application/json';charset=UTP-8'
  },
  data:{
  	name:'sewon',
    	age:20
  }

  axios(options)
  	.then(response => console.log(response))
```

### 1. axios
- Promise API 활용 >> HTTP 비동기 통신 라이브러리
