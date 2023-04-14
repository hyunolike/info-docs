## Postman 스크립트
> [참고자료](https://inpa.tistory.com/entry/POSTMAN-%F0%9F%92%BD-%ED%85%8C%EC%8A%A4%ED%8A%B8-%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%9E%91%EC%84%B1%ED%95%98%EA%B8%B0)
- ![image](https://user-images.githubusercontent.com/61215550/231934948-ddd3d783-0457-498d-8121-df28b40e2360.png)
- 포스트맨 `Node.js` 기반의 런타임 포함 ⭐
  - `Request` `Collection` 동적으로 동작 추가 가능
  - 동적 매개변수 및 요청 간 데이터 전달 가능해짐
### ✔ 2가지 이벤트 흐름
#### `Pre-request Script`
> 요청이 서버로 가기 전 실행
- Request 헤더 key 추가
- url 매개변수 문자열 추가
#### `Test Script`
> 요청이 서버로 간 후 응답이 반환된 후 실행
- test 함수 사용
- .response .expect 객체 등에 접근 가능


