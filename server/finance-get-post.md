## 금융권 HTTP Method - `GET` `POST`
> [참고자료](https://mydata.kftc.or.kr/web/mydataApi/api)
### 금융결제원 마이데이터 중계 서비스
- 마이데이터 표준 API 종류
  - 정보제공 API 
  - 인증 API
  - 지원 API
- 데이터 표현 규격
  - JSON
  - UTF-8
- 데이터 통신 규격
  - TLS(Transport Layer Security): 안전한 통신을 위한 보호 방안 / TLS 기반 상호인증 및 전송구간 암호화 사용
  - REST(Representational State Transfer): 보안상 이유로 `GET` `POST` 만 제한적 사용 ⭐
- 개인신용정보 전송요구 인증 규격
  - Oauth(Open Authentication) 2.0
- 접근토큰 규격
  - JWS(JSON Web Signature)

### ✔ `GET``POST`
> [참고자료](https://stackoverflow.com/questions/198462/is-either-get-or-post-more-secure-than-the-other)
- 둘 다 **자체 보안** 제공하지 않음 !!
#### `POST` 방식이 더 안전한 이유
- Search spiders and web accelerators
- Confused deputy attack
- Proxy logs
- Proxy cache
  - GET 응답 보유 / POST 보유 안함
- HTTP "Referer"
  - GET 요청에 대한 응답으로 제공된 페이지에서 다른 페이지 이동 시 >> 타사 웹사이트는 모든 GET 요청 매개변수 볼 수 있음
- Broswer history
  - GET 요청은 매개변수와 함께 브라우저 기록 저장
  - 공격자 쉽게 접근 가능 ㅠ,ㅠ
- Browser refresh action 브라우저 새로 고침
  - 새로 고침 누르는 동시에 GET 요청 실행 / POST는 요청 재시도 안함
#### 결론
- 주로 데이터만 변경 시 POST 사용 하자
- 로그인 양식에는 POST 요청만
