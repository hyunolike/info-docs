## 1. 동일 출처 정책 `Same Origin Policy(SOP)` - 브라우저 강제적 SOP 기본으로...
> [참고 자료](https://developer.mozilla.org/ko/docs/Web/Security/Same-origin_policy) <br>
> [참고 자료 ✔](https://yoo11052.tistory.com/139)
- 브라우저는 기본적으로 내 서버가 아닌 다른 서버에서 받아온 데이터는 차단!
- `A 사이트` <-----❌-----> `B 사이트`   
  - `ajax()` 메서드 >> 서로 다른 도메인의 데이터 전송 불가 / 교차 도메인 허용 x
- `출처` >> 2개의 URL(프로토콜, 포트(명시한 경우), 호스트) 모두 동일 >> 동일한 출처 ✔
- SOP의 빡빡한 정책 >> 외부에서 데이터 못불러옴 >> ⭐하지만, `CSRF` `XSS` 같은 보안 취약점 공격으로부터 안전하다는 장점!


## 2. SOP를 풀어주는 `CORS` - 교차 출처 리소스 공유
- CORS >> 서로다른 출처간에도 요청과 응답 허용하는 정책
- 크게 2가지 방식
  - `Simple Request`
  - `Preflight Request`
### 2.1 `Simple Request`
- 만족해야 하는 조건
  - HTTP Method >> GET, POST, HEAD 중 하나
  - `Content-Type` 헤더가 다음 중 하나 >> 
    -  `application/x-www-from-urlencoded` 
    -  `multipart/form-data` 
    -  `text/plain`
  - `CORS-safelisted request-header` 포함하는 경우(Fetch spec)
  - `XMLHttpRequest.upload`에 이벤트 핸들러, 리스너 등록 x
  - `ReadableStream` 객체 포함되지 않은 경우
- 동작 방식
  1. 사용자가 요청 헤더에 자신의 Orgin을 실어서 서버로 요청
  2. 서버는 요청 헤더의 Origin 확인
  3. CORS 요청 유효 >> 서버는 응답 헤더에 `Access-Control-Allow-Origin` 헤더 추가해 사용자에게 다시 전송

### 2.2 `Prefilght Request`
- `Simple Request`의 조건 만족 x >> 브라우저가 자동 생성
