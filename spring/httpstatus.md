## `HttpStatus` 상태코드 - 커스텀 예외처리
> [참고자료](https://tecoble.techcourse.co.kr/post/2020-08-31-http-status-code/)

- 상태코드: 클라이언트 <--> 서버 간의 통신 상태를 나타내는 약속된 코드
  - 50여 개의 3자릿수 코드 존재!
  - `1xx`: 정보 응답
  - `2xx`: 성공 응답
  - `3xx`: 라디이렉트
  - `4xx`: 요청 오류
  - `5xx`: 서버 오류

### 1. 대표적 코드
```
200 OK - 요청 성공
201 Created - 요청에 따른 새로운 리소스 생성 성공
204 No Content - 요청은 성공했지만 딱히 보내줄 내용이 없음
400 Bad Request - 잘못된 요청
401 Unauthorized - 비인증 요청
403 Forbidden - 비승인 요청
404 Not Found - 존재하지 않는 리소스에 대한 요청
500 Internal Server Error - 서버 에러
503 Service Unavailable - 서비스가 이용 불가능함
```

### 2. `ControllerAdvice`
- 일반적으로 `5xx` 코드는 클라이언트에게 보여주면 안됨! ✔
  - 서버 측에서 처리하거나 의미 있는 `4xx` 에러로 변환해 전달!! ⭐

### 3. `401` vs `403`
- `401`: 권한 없음 >> 인증의 개념!
- `403`: 금지된!! >> 사용자가 권한 밖의 요청을 했을 때 전달

