## `localStorage` `sessionStorage`
> [참고자료](https://ko.javascript.info/localstorage)
- 웹스토리지 객체 >> 브라우저 내에 키-값 쌍을 저장할 수 있게 해줌
- 쿠키이외 다른 방식 사용하는 이유 
  - 쿠키와 다르게 웹스토리지 객체 >> 네트워크 전송 시 >> 서버로 전송 x
  - 서버가 HTTP헤더를 통해 스토리지 객체를 조작할 수 없다는 점 >> 웹 스토리지 객체 모두 자바스크립트 내에서 수행
  - 웹 스토리지 객체 >> 도메인, 프로토콜, 포트로 정의되는 오리진에 묶임 >> 프로토콜과 서브 도메인이 다르면 데이터에 접근 불가 ㅠ,ㅠ
- ![image](https://user-images.githubusercontent.com/61215550/178433469-a310f13d-8620-4002-b429-33b9cf163789.png)
- ![image](https://user-images.githubusercontent.com/61215550/178433509-8a3be9d7-919f-46ec-9559-dea482aebf1d.png)
