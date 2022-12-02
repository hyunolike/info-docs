## 하이퍼바이저 - 가상화 & 가상머신
> [참고자료](https://velog.io/@yeongori/%EA%B0%80%EC%83%81%EB%A8%B8%EC%8B%A0%EC%9D%B4%EB%9E%80)
- ✔핵심
  - 가상 머신 >> 말 그대로 실체가 없는 또다른 컴퓨터
  - Hypervisor >> 핵심 역할
  - Hypervisor >> 리소스 나눠주는 소프트웨어

### 1. 가상화
> 실제 존재하지 않는 컴퓨터 😛
- 물리적 컴퓨터 자원 `cpu` `memory` `disk` 등 추상화 
- 추상화된 자원 이용 >> 가상의 컴퓨터 만들기 >> 가상머신

### 2. 하이퍼바이저
- 가상머신 생성 및 구동하는 소프트웨어
- 하이퍼바이저 운영 체제, 가상 머신의 리소스 분리 >> VM 생성 및 관리 지원!

#### 2-2. 하이퍼바이저 유형
> [참고자료](https://lovejaco.github.io/posts/two-types-of-hypervisors/)
- ![image](https://user-images.githubusercontent.com/61215550/205227847-3d7bcdaa-0e5f-4d3e-8b31-69bc1fbf5fa9.png)
- ✔ 호스트: 하이퍼바이저로 사용되는 물리 하드웨어 
- ✔ 게스트: 리소스 사용하는 여러 VM
##### 유형1 `네이티브` `베어 메탈 하이퍼바이저` - 하드웨어 위에서! 📌
- ![image](https://user-images.githubusercontent.com/61215550/205227479-0952b9c6-db18-4fd1-a779-558363c7bcc3.png)
- 호스트의 `하드웨어` 직접 구동 >> 게스트 운영 체제 관리
- 엔터프라이즈 데이터 센터 & 서버 기반 환경 >> 일반적 사용

##### 유형2 하이퍼바이저 - 운영체제 위에서! 📌
- ![image](https://user-images.githubusercontent.com/61215550/205227545-44e506ec-2898-4fc5-8493-c0d3807141d0.png)
- 기존 운영체제에서 `소프트웨어 레이어` 또는 `애플리케이션` 으로서 구동


