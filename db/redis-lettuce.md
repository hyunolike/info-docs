## Redis / java client `Lettuce`
> [참고자료](https://jojoldu.tistory.com/418)
- 레디스 소개
  - Memory 저장하는 오픈소스 디비 소프트웨어
  - 데이터 휘발성
  - 빠른 접근
- 😛 Redis 자바 클라이언트 종류
  - `Jedis`
  - `Lettuce` >> 이걸 사용하자!! 😱
### Lettuce
- 고성능
- 확장 가능
- 스레드 안전
- `Netty` 프레임워크 위에 빌드된 비동기 이벤트 기반 네트워크 애플리케이션 프레임워크
- 다중 연결 처리
- 강력하고 유연한 api

#### 핵심 기능
##### 1. 커넥션 핸들링
- standalone 연결 / 커넥션 풀의 일부인 커넥션 오브젝트 통해 Redis로의 커넥션 관리
- 커넥션 >> 논블로킹 / 여러 스레드드로가 효율적으로 동작 + 디자인
##### 2. 동기, 비동기, 리엑티브 api
##### 3. 클러스터 지원
- 분산된 레디스 셋업과 상호작용할 수 있는 api
- 클러스터 노드 자동 발견
- 토폴로지 변경 지원
- 적절한 노드로 명령 라우터
##### 4. Sentinel 지원
##### 5. 레디스 고급 지원
- 파이프라이닝, 트렌젝션, 루아스크립팅과 같은 고급 기능 지원
- 스트림, 위치 기반 정보 인덱싱, Redis 모듈 api >> Redis 데이터 구조 및 명령에 대한 지원 제공
##### 6. 코덱 `Codes`
- 데이터 어떤 형식 저장 >> 직렬화, 역직렬화 기법 직접 선택 가능
##### 7. 자동 재연결 & 타임아웃 핸들링
##### 8. 리소스 관리