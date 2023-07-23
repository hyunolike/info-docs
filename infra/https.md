## HTTPS 원리 이해
> [참고자료](https://brunch.co.kr/@growthminder/79)
- HTTPS > HTTP 프로토콜 + 암호구간(SSL/TLS) 얹은 프로토콜
- 인증서 통해 서버 진위 파악 + 서로 함께 알 수 있는 암호화 키 사용 데이터 보호
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/9e504139-0214-4513-a156-74b1cd90ed09)

### 1. SSL/TLS 핸드세이크 전체 흐름
- <img width="942" alt="image" src="https://github.com/hyunolike/info-docs/assets/61215550/c7a6cffa-9906-45bc-800b-f3f1fc8b54db">
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/d454173e-53bb-4a05-9e2e-c9ed2b659ca8)

### 2. 대칭/비대칭 키 암호화
- SSL/TSL > 대칭 & 비대칭 키 암호화 방식 > 혼합한 하이브리드 방식
- 속도 & 보안 동시 장점
  - 속도 > 데이터 암/복호화 공통키(대칭키) 사용 (세션키, MAC 키)
  - Pre Master Secret > 비대칭키 사용
- ⭐️ 비대칭키(Pre Master Secret) 사용해 공통키(세션키, MAC 키) 전달, 공통키 각자 만들어 데이터 암호화하는데 사용
#### 2-1. 대칭키
- 서버, 클라이언트 > 동일한 키
- 예. 엑셀 비밀번호
#### 2-2. 비대칭키
- 예. 인증서
- 서버 > 퍼블릭/프라이빗 키 쌍 생성
