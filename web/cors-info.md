## cors
> [참고자료](https://velog.io/@betterfuture4/CORS-%EA%B0%9C%EB%85%90-%EC%A0%95%EB%A6%AC)
### ✔ ORIGIN
- URL 아래 3가지 모두 같은 경우
  - 프로토콜
  - 호스트
  - 포트
### SOP `Same Origin Policy`
- 다른 출처 리소스 사용 제한하는 `보안 방식`
### CORS `Cross-Origin Resorce Sharing` 
- 다른 `origin` (도메인, 프로토콜) 등으로 들어오는 요청 허용해주는 것
- ⭐ 추가 http 헤더 사용 > 한 출처에서 실행 중인 웹 > 다른 출처의 선택한 자원 접근 권한 부여

### ⭐ 접근 제어 시나리오
1. Simple Request
  - 사전 요청 `Preflight` 없이 바로 요청 날림
2. Preflight Request
  - 예비요청 + 본요청
3. Credentialed Request
  - 자격 증명(쿠키, `authorization`, 인증서 ...) 포함하는 요청
4. 추가 헤더
  - `Access-Control-Expose-Headers`: 웹 브라우저의 클라이언트 스크립트에 노출될 헤더 결정


