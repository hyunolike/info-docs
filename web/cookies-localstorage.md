## Cookies vs LocalStorage
> [참고자료](https://erwinousy.medium.com/%EC%BF%A0%ED%82%A4-vs-%EB%A1%9C%EC%BB%AC%EC%8A%A4%ED%86%A0%EB%A6%AC%EC%A7%80-%EC%B0%A8%EC%9D%B4%EC%A0%90%EC%9D%80-%EB%AC%B4%EC%97%87%EC%9D%BC%EA%B9%8C-28b8db2ca7b2)

### Cookies
> 작지만 강력
- 최대 4kb 용량을 가진 매우 작은 데이터
- 사용 예시
  - 방문한 페이지 저장
  - 유저의 로그인 정보 저장 ..
  - `문자열`만 저장

#### 쿠키 2가지 유형
##### 1. persistent cookies
- 만료일 가짐
- 만료일까지 유저의 디스크에 저장 만료일 지나면 삭제
- 사용 예시 >> 유저 경험을 커스텀!! / 특정 웹사이트에서 행동 기록 등...
##### 2. session cookies
- 만료일 포함 x 
- 브라우저나 탭 열린 동안 유지
- 브라우저 닫히면 영구적 삭제
- 사용 예시 >> 😛 은행 유저들의 자격 증명 저장하는데 사용

### 로컬 스토리지
> 영구적인 솔루션
- `html5` 이후
- HTTP 요청에서 데이터 주고받을 필요 없음
- 촤대 5Mb 정보 저장 가능
- `persistence cookies` 처럼 동작
### ⭐ 결론
- 쿠키 >> HTTP 요청과 함께 서버 요청 다시 전달
- 로컬스토리지 >> 더 크고 / 클라이언트 측 정보 저장 가능
