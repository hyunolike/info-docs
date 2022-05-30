## 컨테이너 런타임
> [참고 자료](https://www.aquasec.com/cloud-native-academy/container-security/container-runtime/)
- 호스트 운영 체제에서 컨테이너를 실행할 수 있는 소프트웨어 구성 요소
- 컨테이너화된 아키텍처에서 컨테이너 런타임 
  - 리포지토리에서 컨테이너 이미지 로드
  - 로컬 시스템 리소스 모니터링
  - 컨테이너 사용을 위한 시스템 리소스 격리
  - 컨테이너 생명 주기
- 공통 컨테이너 런타임
  - 일반적으로 컨테이너 오케스트레이터와 함께 작동
  - 오케스트레이터: 컨테이너 클러스터 관리 담당 / 컨테이너 확장성, 네트워킹 및 보안과 같은 문제 처리
  - 컨테이너 엔진: 클러스터의 모든 컴퓨팅 노드에서 실행되는 개별 컨테이너 관리 담당
- 컨테이너 런타임의 일반적인 예. 
  - `runC`
  - `containerd`
  - `Docker` `Window` 컨테이너
- 컨테이너 런타임 유형
  1. 하위 수준 런타임
  2. 상위 수준 런타임
  3. 샌드박스 또는 가상화된 런타임

### 컨테이너 런타임 유형
- ⭐ `OCI(Open Container Interface)`: Linux 컨테이너에 대한 개방형 표준을 제공하는 것을 목표로 Docker에서 시작한 Linux Foundation 프로젝트
  - 주요 프로젝트: 2015년 출시 `runC` >> OCI 사양을 구현하는 저수준 컨테이너 런타임
  - 이를 기반으로 컨테이너 런타임 엔진의 기초 형성!!
#### 1. 저수준 컨테이너 런타임
- 컨테이너 생성 및 실행 담당 ✔
- 컨테이너화된 프로세스 실행되면 컨테이너 런타임은 다른 작업 수행할 필요 없음
  - Linux 기본요소 추상화, 추가 작업 수행하도록 설계 ❌

|용어|설명|
|-----|-----|
|`runC`|Docker 및 OCI에서 생성 <br> Go 언어로 작성|
|`crun`|Redhat 주도하는 OCI 구현 <br> C 언어로 작  <br> 가볍고 성능 좋음 / cgroup v2를 지원하는 최초의 런타임 중 하나|
|`containered`|Linux 및 Window에서 지원하는 오픈 소스 데몬으로 __API__ 요청을 통해 컨테이너 수명 주기 관리 용이 <br> containerd API >> 추상화 계층 추가 및 컨테이너 이식성 높임|

#### 2. 고급 컨테이너 런타임
- 아래는 인기 고급 런타임 예시

|용어|설명|
|-----|------|
|`Docker(Containerd)`|유무료 옵션과 함께 전체 기능 제품군을 제공하는 최고의 컨테이너 시스템 <br> 기본 Kubernetes 컨테이너 런타임|
|`CRI-O`|rkt 및 Docker에 대한 경량 대안을 제공하는 Kubernetes의 CRI(컨테이너 런타임 인터페이스)의 오픈 소스 구현|
|`Windows 컨테이너 및 Hyper-V 컨테이너`|Window Server에서 사용 가능한 Window VM에 대한 2가지 경량 대안 <br>- `Window 컨테이너`: 추상화(Docker와 유사) 제공<br>- `Hyper-V 컨테이너`: 가상화 제공|

#### 3. 샌드박스 및 가상화된 컨테이너 런타임
- OCI >> 샌드박스 및 가상화 구현에 대한 사양 포함