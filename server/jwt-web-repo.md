## `JWT` 웹 저장소별 차이
> [참고자료](https://velog.io/@mygomi/JWT%ED%86%A0%ED%81%B0-%EC%96%B4%EB%94%94%EC%97%90-%EC%A0%80%EC%9E%A5%ED%95%A0-%EA%B2%83%EC%9D%B8%EA%B0%80-%EC%9B%B9-%EC%A0%80%EC%9E%A5%EC%86%8C%EB%B3%84-%EC%B0%A8%EC%9D%B4)

### 1. 고려할 점
- 얼마나 오래 보관? - 저장소별 차이 !! ✔
  - `세션 스토리지`: 저장된 데이터는 브라우저 닫으면 제거 / 자동 로그인 등 브라우저 열었을 때도 유지해야 하는 데이터 보관 어려움
  - `로컬스토리지` : 영구 저장소 / 따로 지워주지 않으면 브라우저에 계속 남아있음 / 중요한 정보 넣어두면 위험
  - `쿠키`: 만료일 지정 가능 / 만료일 경과되면 삭제
- 얼마나 많은 정보 보관? - 저장소별 차이 !!
  - `쿠키`: 개수 & 용량 차이 / 최대 4KB / 하나의 사이트에 최대 20개 쿠키만 가능
  - `로컬스토리지`: 5MB / 쿠키보다 더 많은 정보 저장 가능
- 보안위험 대비 - `토큰`: 정당한 사용자 여부 판단할 수 있는 도구 >> 사용자인 척 가능 ㅋㅋㅋㅋㅋ
  - `로컬스토리지`: Javasript 통해 쉽게 접근 가능 >> XSS 공격 취약 / 쿠키는 `httpOnly` 플래그 설정해서 예방 가능 / 쿠키가 모든 웹 요청에 함께 전송(`Secure flag` 설정하면 보안되지 않은 연결에서 전송 x)
  - `쿠키`: 여러 옵션 추가 설정 시 로컬스토리지의 취약점 보완 가능 / ... 어떤거에 담을지는 각자의 판단 필요
- 기타 트래픽 문제
  - 모든 웹 요청은 쿠키정보를 포함하여 서버 전송
