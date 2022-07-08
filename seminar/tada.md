## 타다 - 시스템 아키텍처
> [참고 자료](https://engineering.vcnc.co.kr/2019/01/tada-system-architecture/)

### 1. 사용 기술
- `Kotlin`
  - JVM 무시 X >> 비교적 새로운 JVM 기반 언어인 Kotlin / Spring boot에 쉽게 적용 / 커뮤니티 적극 권장
- `Spring Boot` 
  - 보일러 플레이트 코드 작성 줄이고 서비스 개발 집중 / SQS 메시지 처리, HTTP 요청 및 응답으로 Protocal Buffers 메시지 사용 등 제공 기능 많음
- `Kubernetes`
  - 컨테이너 오케스트레이션 플랫폼 / 배포 자동화 & 스케일링 등 여러 가지 운영적인 편의성 제공
- `gRPC`
  - 실시간성이 중요한 차량 위치나 운행 상태 변화 등은 `Streaming` 사용 / 서비스 개발 집중 및 관리 오버헤드 감소위해 사용
- `Redis`
  - 서버 간 메시징 기술 `Pub/Sub` >> Redis만이 `ElastiCache` 이용해  쉽게 띄우고 관리 가능
- `Protocol Buffers`
  - gRPC뿐 아니라 HTTP/2로 주고받는 메시지 정의할 때도 사용 / 따로 문서화 하지 않고 proto 파일을 공유 >> 더욱 명확하고 편리하게 API 명세 공유 가능
- `Terraform` 
  - HCL 이용해 인프라스트럭처 프로비저닝 및 관리 편리하게 해주는 도구
### 2. 사용 중인 AWS 서비스들
- `EKS`
  - Kubernetes 클러스터의 마스터 노드들을 쉽게 띄우고 관리해주는 서비스 
- `ECR`
  - 서버 배포 시 __Docker Gradle Plugin__ >> docker 이미지 생성 >> ECR 푸시 >> (helm) 명령어 통해 쿠버네티스 배포
- `SQS`
  - 배차 요청 처리하기 위해 SQS 이용
- `RDS`
  - 타다 서비스의 데이터는 `Aurora` 저장 / DB 배포 및 관리 쉬워짐
- `Kinesis`
  - 실시간 차량 위치 정보 및 로그를 수집하기 위해 사용
- `Firehose`
  - 로그 저장
### 3. 시스템 구성
![image](https://user-images.githubusercontent.com/61215550/177898547-68b96a8f-dc0f-40ee-ad1b-c7791c4c14ab.png)
