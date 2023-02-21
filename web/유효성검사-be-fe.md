## 유효성검사 - ⭐ 프론트 & 백엔드 양쪽에서 검증 코드 작성!
> [참고자료](https://velog.io/@beberiche/%EC%9C%A0%ED%9A%A8%EC%84%B1-%EA%B2%80%EC%82%AC%EB%8A%94-%EC%96%B4%EB%94%94%EC%97%90%EC%84%9C-%ED%95%B4%EA%B2%B0%ED%95%B4%EC%95%BC%ED%95%98%EB%82%98)
- 데이터가 서버 혹은 데이터베이스 옮겨지기 전, 개발자가 만든 조건에 부합하는지 확인, 검증하는 작업
- ![image](https://user-images.githubusercontent.com/61215550/220221053-9b34567c-ba6a-4f8d-b53e-fc99dbf0b31d.png)

### 0. 양측에서 검증해야 되는 이유
> 😛 반응 속도 차이 발생
- ![image](https://user-images.githubusercontent.com/61215550/220220989-ab109311-d772-4474-a42a-992a4a0270a1.png)
- ![image](https://user-images.githubusercontent.com/61215550/220220964-c1fd7b07-31b1-4007-af19-c40841bb2bfa.png)
- (프론트엔드 유효성 검사) 폼 작성 > `프론트엔드 유효성 검사` > 오류 메시지 
- (백엔드 유효성 검사) 폼 작성 > 전송 > `백엔드 유효성 검사` > (오류 발생) > 클라이언트 전송 

### 1. 클라이언트 측
- ✔ 가장 많이 사용되는 유효성 검사 `Form Validation`

### 2. 서버 측
- ✔ 서버의 경우 다양함!
  - `route`
  - `model` 내
  - `controller` 

### 3. 장단점
- 처리속도는 클라이언트가 빠름
- 서버에서만 할 수 있는 유효성 검사들도 존재
