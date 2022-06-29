## `ECDH` `ECDSA`
> [참고 자료](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=tnrud3579&logNo=221456223834)
- 타원곡선 디피 헬만 `ECDH` ✔
  - 공개키 영구적 >> `ECDH`
  - 공개키 일시적 >> `ECDHE`

### 1. ECDSA - `디지털 서명`
- 디지털 서명 >> 메시지 + Private key 
- 메시지 검증 >> 메시지 + 디지털 서명 + Public Key 
  - 해당 메시지 Key 소유자에 의해 서명된 것인지 체크
  - 메시지는 오직 Private Key 소유자에 의해서만 서명

### 2. ECDH(동일한 대칭키 사용자 A, 사용자 B 공유) - `암호화 `
> 키교환 알고리즘
- 개인키: `{1, ..., N - 1}` 선택된 임의의 정수 d
- 공개키: 점 `H = dG` (G는 하위 그룹의 기준점)
  - d(개인 키),G를 안다면 개인 키 d를 찾는 것 쉽다
  - H와 G 안다면 개인 키 d를 찾는 것 어렵다
- 사용자 A: 개인키 + B의 공개키 ✔ 공통된 시크릿 키 도출
- 사용자 B: 개인키 + A의 공개키 ✔ 공통된 시크릿 키 도출
