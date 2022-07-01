## Prometheus
> [참고 자료](https://medium.com/finda-tech/prometheus%EB%9E%80-cf52c9a8785f) <br>
> 오픈소스 모니터링 툴
- SoundCloud 사에서 만든 오픈소스 시스템 모니터링 및 경고 툴 킷 
- Kubernetes에서도 Prometheus 사용 장려
- __대상 시스템__ 으로 부터 각종 모니터링 지표를 수집하여 저장하고 검색할 수 있는 시스템
  - 구조 간단 / 운영 쉬움 / 강력한 쿼리 기능 / 그라파나의 시각화 지원 / 다양한 플러그인
  - 쿠버네티스의 메인 모니터링 시스템으로 많이 사용!

### 1. 아키텍처
> `Prometheus & Grafana` `Elasticsearch & Kibana`
- ![image](https://user-images.githubusercontent.com/61215550/176803946-99f280f7-bbc6-4bc9-825b-65a38b0d57c9.png)
- ![image](https://user-images.githubusercontent.com/61215550/176804794-ebc7b616-2c88-426d-a9c6-97bb73e84941.png)
- ![image](https://user-images.githubusercontent.com/61215550/176805101-29f95f68-f596-4db3-903c-6ce9a2f71d37.png)

### 2. 기본 구조 
> [참고 자료](https://owin2828.github.io/devlog/2020/03/13/etc-5.html)
#### 2.1 `Metric` 수집
- 수집 대상 >> `Target System` 
  - 예. MySQL, Tomcat, VM 등
- 해당 대상의 메트릭을 프로메테우스에 전송하기 위해서는 >> `Exporter` 사용

#### 2.2 `pulling` 방식
- 프로메테우스가 Target System에서 메트릭  수집하는 방식 __폴링__ 방식 ✔
- 주기적으로 `Exporter` 로부터 메트릭 읽어와서 수집하는 방식
- `push` 방식은 서비스가 오토 스켈링등으로 가변적일 떄 유리 ⭐
- `polling` 방식은 모니터링 대상이 가변적으로 변경할 경우, 모니터링 대상의 IP 주소들을 알 수 없다는 단점 ㅠ,ㅠ 어려운 점
  - 이를 해결 `서비스 디스커버리` 방식: 특정 시스템이 현재 가동중인 서비스들의 목록과 IP주소를 가지고 있으면 됨

#### 2.3 `Service Discovery`
- 프로메테우스 >> 서비스 디스커버리 시스템과 통합하도록 되어 있음
- `DNS`, `Consul` `쿠버네티스` >> 모니터링해야할 타겟 서비스의 목록 가져올 수 있음

#### 2.4 `Exporter`
- 모니터링 에이전트: 타겟 시스템에서 메트릭 읽어 프로메테우스가 풀링 할 수 있도록 해줌
- `HTTP GET`으로 메트릭을 텍스트 형태로 리턴
- 요청 당시 데이터 리턴 / Exporter 자체의 기본값(히스토리) 저장하는 기능 x

#### 2.5 `Retrieval`
- 서비스 디스커버리 시스템 >> 모니터링 대상 목록 가져옴
- Exporter >> 주기적으로 그 대상으로부터 메트릭 수집
- 서비스 디스커버리 시스템 + Exporter 하는 모듈 = `Retrieval`

#### 2.6 저장
- 수집된 정보 >> 프로메테우스 내 메모리 & 로컬 디스크
- 이중화, 클러스터링 불가(클러스터링 대신 샤딩)

#### 2.7 서빙
- 저장된 메트릭 >> `PromQL 쿼리` 언어 이용해 조회 가능
- 외부 API or 프로메테우스 웹콘솔 이용해 서빙 가능

#### 2.8 기타...
- `gateway`: 메트릭 수집
- `Alert manager`: 알람

### 3. 장/단점
#### 3.1 장점
- `PULL` 방식 구조 / 모든 메트릭의 정보를 중앙 서버로 보내지 않아도 됨
  - 대부분의 모니터링 구조 `PUSH` 방식 >> 각 타겟 서버에서 부하 걸릴 경우 PUSH 방식은 fail point 
- Kubernetes 환경에서 설치 간단 / grafana와의 연동을 통한 운영 쉬움
- 다양한 metric exporter 제공
  - Linux, Window등의 OS metric 뿐 아니라 각종 `Third-party`의 exporter 제공
- 장기간 데이터 유지 및 확인
  - 데이터 저장소 `시계열 데이터` 구성 >> 많은 양의 정보 빠르게 검색 가능
#### 3.2 단점
- ![image](https://user-images.githubusercontent.com/61215550/176815391-59aaf87d-b02a-49c7-84eb-899bb24bc741.png)
- 위 그림이 공식적으로 지원하는 다중화 방식 (`Clustering` 과 거리가 멈)
  1. 각 Region에 프로메테우스 배치 
  2. 이를 Master에 Aggregate하는 방식
- 싱글 호스트 아키텍처 >> 저장용량 부족하면 >> 디스크 용량 늘리는 것뿐!
- 프로메테우스 서버 다운, 설정 변경 등을 위해서 재시작 할 경우 >> 그간 metric 유실 
- 일정 풀링 주기 기반으로 metric 가져옴 >> 풀링 순간 스냅샷 정보만 알 수 있음
  - 스냅샷의 연속된 모음이기 때문에 근사값의 형태
