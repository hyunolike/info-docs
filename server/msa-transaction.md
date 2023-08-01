## msa 트랜잭션
> [참고자료](https://taes-k.github.io/2020/10/28/msa-3/)
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/e0e69c7a-19dd-42f3-98b1-724b99f31824)

### 1. XA 분산 트랜잭션
- `x-open` 표준 기술
- 동기 IPC 유지
### 2. ✔ SAGA 패턴
- 데이터 일관성 유지위한 패턴
- 보상 트랜잭션 > 롤백
- 디비 트랜잭션 사용 x > 자동 롤백 아님!
- 다중 디비 환경에서 데이터 일관성 유지
### 3. Choreography SAGA
- 각각의 이벤트 구독
- 장점
  - 단순 연결
  - 느슨한 연결
 - 단점
   - 구현 로직 분산
   - 순환 의존
   - 강한 연결성
### 4. Ochestration SAGA
- SAGA 참여 서비스 지휘
- 모든 서비스 흐름 관장
