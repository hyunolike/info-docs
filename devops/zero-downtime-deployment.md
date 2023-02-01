## 무중단 배포 아키텍처
> [참고자료](https://www.samsungsds.com/kr/insights/1256264_4627.html)
- 😛 로드밸런서 핵심!
### 1. 무중단 배포
- 운영 중 서비스 중단 x >> 신규 소프트웨어 배포하는 기술
- 무중단 배포 핵심 ⭐ - 고가용성 시스템 인프라 구성
  - `로드밸런서`
  - 인스턴스 트래픽 제어 배포

### 2. ✔ 무중단 배포 2가지
#### 2-1. 롤릴 배포 `Rolling Deployment`
- 사용 중인 인스턴스 내에서 새 버전을 점진적으로 교체하는 것 >> 무중단 배포의 가장 기본적인 방식
- ![image](https://user-images.githubusercontent.com/61215550/215941561-0f3723a3-f877-46df-a66d-b9e8eb0523ec.png)

#### 2-2. 블루-그린 배포 `Blue-Green Deployment`
- `로드밸런서` 통해 신버전으로 모든 트래픽 전환하는 배포 방식
- ![image](https://user-images.githubusercontent.com/61215550/215941692-4e510d6a-1312-46e2-92da-180350cc53ed.png)

#### 2-3. 카나리 배포 - `모니터링 & 검증` 초점!
- 잠재적 문제 상황 미리 발견하기 위한 방식
- 신버전의 제공 범위 늘려가면서 모니터링 및 피드백 과정 거칠 수 있음 
- `로드밸런서` 통해 신버전의 제품을 경험하는 사용자 조절할 수 있는 것! ⭐
- ![image](https://user-images.githubusercontent.com/61215550/215942001-76aa3e14-f443-4a86-8dc0-3e2773204f23.png)
