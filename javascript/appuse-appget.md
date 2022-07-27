## `app.use()` `app.get()`
> [참고자료](http://daplus.net/node-js-express-js%EC%97%90%EC%84%9C-app-use%EC%99%80-app-get%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90/)


|`app.use()`|`app.get()`|
|------------|-----------|
|route 모듈화 하는데 사용|GET method 사용|
|`middleware` 바인딩 위한 목적|`GET HTTP` 요청 시 특정 경로 처리 위한 목적|
|미들웨어 기능 요청된 경로와 베이스 경로가 일치할 때 실행|지정된 콜백 함수 사용|
|해당 경로와 일치하는 모든 HTTP 요청 허용|해당 특정 경로에 대한 HTTP GET 요청만 허용|
|`app.use([path,],callback[,callback ...])`|`app.get(path, callback)`|


- ![image](https://user-images.githubusercontent.com/61215550/181137312-3bbd2b84-4e6b-4e02-9b16-337d7af6883b.png)
