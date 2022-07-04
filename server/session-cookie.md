## 세션, 쿠키, JWT
> HTTP 프로토콜 특성, 약점 보완하기 위해서 사용 `connectionless` `stateless`  / ✔ 서버는 매번 클라이언트가 누구인지 확인 ㅠ,ㅠ <br>
> [참고 자료](https://interconnection.tistory.com/74#:~:text=1.%20HTTP%EC%9D%98%20%ED%8A%B9%EC%A7%95%EA%B3%BC%20%EC%BF%A0%ED%82%A4%EC%99%80%20%EC%84%B8%EC%85%98%EC%9D%84%20%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94%20%EC%9D%B4%EC%9C%A0,-%EC%BF%A0%ED%82%A4%EB%A5%BC%20%EB%B0%9C%EA%B8%89&text=%EA%B8%B0%EB%B3%B8%EC%A0%81%EC%9C%BC%EB%A1%9C%20HTTP%20%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C%20%ED%99%98%EA%B2%BD,%EC%84%B8%EC%85%98%EC%9D%84%20%EC%82%AC%EC%9A%A9%ED%95%98%EA%B2%8C%EB%90%A9%EB%8B%88%EB%8B%A4.) <BR>
> [세션 쿠키 토큰](https://tofusand-dev.tistory.com/89)

### 1. 쿠키
- 클라이언트(브라우저) 로컬에 저장되는 키와 값이 들어있는 작은 데이터 파일

### 2. 세션
- 세션은 쿠키 기반, 사용자 정보 파일을 브라우저에 저장하는 쿠키와 달리 세션은 서버 측에서 관리

### 3. 쿠키, 세션 차이
- 동작원리 비슷, 세션도 결국 쿠키를 사용
- 큰 차이점 저장 위치
  - 쿠키: 서버의 자원 사용 x
  - 세션: 서버의 처리 필요
