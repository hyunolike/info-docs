## 배포 전략
> [참고자료](https://dev.classmethod.jp/articles/ci-cd-deployment-strategies-kr/)
- `AWS`

### 1. In-place Deployment
- 사용 중인 환경에 새로운 변경사항이 포함된 애플리케이션만 반영하는 방법

### 2. Rolling Update Deployment
- 여러 개의 가동중인 서버(인스턴스)를 갖춘 환경에서 한 번에 정해진 수만큼 서버에 새로운 변경 사항이 포함된 어플리케이션 배포하는 방법

### 3. Blue/Green Deployment
- 새로운 변경사항이 포함된 어플리케이션을 위한 새로운 환경을 구축하고 교체하는 방법

### 4. Canary Deployment
- 가동 중인 서버들의 일부에만 새로운 앱을 배포하여, 일부 트래픽을 새 버전의 환경으로 분산하는 방법
