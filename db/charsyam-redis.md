## 우아한 레디스
> 참고자료 - 우아한테크
### 1. Redis 소개
- Open Source 
- In Memory Data Structure Store
- Support data structures
  - String, set, sorted-set, hashes, list
  - Hyperloglog, bitmap, geospatial index
  - Stream
- Only 1 Committer
#### 1.1 Cache
- 나중에 요청 결과 미리 저장 >> 빠르게 서비스
- Factorial (동적 프로그래밍 개념)
- <img width="902" alt="image" src="https://github.com/hyunolike/info-docs/assets/61215550/1e80215d-1d4d-4cfa-9894-4824c249a03c">
- 어디서 많이 사용? 🤗
  - <img width="889" alt="image" src="https://github.com/hyunolike/info-docs/assets/61215550/16e34a4f-704d-4157-b3f9-f9f45ffcab56">
- 파레토 법칙 
  - 전체 요청의 80% >> 20%의 사용자
- 캐시 사용 예시 >> 1. 빠른 요청 처리 2. Write Back(캐시 먼저 저장 / 장애 발생시 사라짐..) - 로그 저장시??? 
  - <img width="902" alt="image" src="https://github.com/hyunolike/info-docs/assets/61215550/0e0d2dee-33fb-4a6a-a30a-0ddcaff5c38c">
  - <img width="889" alt="image" src="https://github.com/hyunolike/info-docs/assets/61215550/f4aeb88a-5fdd-4031-bd4c-6b5bf7c3d231">
### 2. Collection 중요한 이유
- 개발의 편의성 / 개발의 난이도
- 개발의 편의성
  - 랭킹 서버 직접 구현한다면?
  - <img width="860" alt="image" src="https://github.com/hyunolike/info-docs/assets/61215550/1c1f8bae-3330-4497-92e6-af5ede615ce6">
### 3. Redis 사용 처
- Remote Data Stroe
  - 서로 다른 서버에서 데이터 공유하고 싶을 때
- 한대에서만 필요한다면, 전역 변수를 쓰면 되지 않을까?
  - Redis 자체 >> Automic 보장
- 주로 많이 쓰는 곳들
  - 인증 토큰 등을 저장(String or hash)
  - Ranking 보드(Sorted Set)
  - 유저 api limit
  - 잡 류(list)
### 4. 레디스 운영
- 메모리 관리 
  - <img width="833" alt="image" src="https://github.com/hyunolike/info-docs/assets/61215550/ebcfc4b2-9183-4e6b-90d1-46956a6764c5">
- O(N) 관련 명령어 주의
- Replication
- 권장 설정 팁
