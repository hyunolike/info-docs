## ⭐CI/CD
![image](https://user-images.githubusercontent.com/61215550/166169407-0532ec40-0fee-4b24-996b-ec6a9c3ac912.png)

### 1. CI/CD
- CI(Continouous Integration) ✔
  - 지속적 통합
  - 소프트웨어 개발하면서 새로운 코드 작성, 코드 변경하고 빌드 및 테스트하여 공유 리포지토리에 통합되는 것
- CD(Continuous Deployment or Continuous Delivery) ✔
  - CI를 통해 테스트까지 모두 끝나고 __배포까지__ 하는 단계
  - `Deployment` 지속적 배포: 배포 단계 __자동화__ / CI 마치고 릴리즈 가능하다면 배포까지 자동으로 이루어질 때 해당 용어 사용!
  - `Delivery` 지속적 제공: 배포 단계 __수동화__ / CI 마치고 릴리즈 가능하다면 배포 단계에서 사람의 검증을 통해 수동적으로 배포가 이루어진다면 해당 용어 사용!
- 사용 예시✌
  - 만약 테스트용 서버에 배포를 한다면 >> `Continuous Delployment`
  - 중요 서비스, 시스템을 고객들에게 배포 한다면 철저한 검증을 통해서 배포 >> `Continuous Delivery`
### 2. CI/CD 툴 
> [참고 자료](https://velog.io/@skyni/CICD-%EA%B0%9C%EB%85%90-%EB%B0%8F-%EA%B0%81%EC%A2%85-%ED%94%8C%EB%9E%AB%ED%8F%BC-%EC%A0%95%EB%A6%AC) <br>
> [27가지 CI/CD 툴](https://ichi.pro/ko/hyeonjae-sayong-ganeunghan-choegoui-ci-cd-dogu-27gaji-194611649728144)
- ✔ 어떤 CI/CD 툴 사용해야 하는가?
  - 사용하기 쉬움
  - 무료 또는 저렴한 수준의 가격
  - AWS EC2 배포 가능
  - Git 연동 가능 
  - 사용자 층 많아서 참고 할 수 있는 자료가 많은 플랫폼
---
- `Github Actions` ✔ ⭐ 요즘 대세ㅋㅋㅋㅋㅋㅋㅋ
  - 복잡한 과정없이 바로 깃허브 사용 가능
  - 빌드 과정 눈으로 확인 가능
  - 젠킨스보다 빠름
  - 문서 부족ㅠ,ㅠ
  - ![image](https://user-images.githubusercontent.com/61215550/166169886-f66b80c0-ef6a-4a51-9fd7-75a0411ddb36.png)

- `Gitlab CI/CD` ✔ 
- `Jenkins` ✔
  - 자바 기반 오픈소스 CI/CD 툴
  - 별도 서버 준비 ㅠ,ㅠ 
  - 규모 작은 프로젝트 추천하지 않음!
- `CircleCI`
- `TeamCity`
  - JetBrains에서 개발한 CI/CD 툴 
  - 자바 기반으로 개발
  - 클라우드와 직접 호스팅을 위한 서버 사용 가능 >> 무료
  - 상업용은 무료 / 이외 기능 유료
- `Buildkite`

### 3. 주요 툴 정리
|명칭|가격|특징|
|-----|-----|-----|
|`Jenkins`|무료 오픈소스 <br>직접 설치해서 서버 운용해야함✔|설치 어려움<br>자바 분야 CI/CD로 뿌리 깊음<BR>다양한 플러그인 제공<BR>파이프라인 구성 자유도 매우 높음|
|`Circle CI`|무료 플랜은 동시에 Job 1개만<br>전문가용은 비싸 ㅠ,ㅠ|`Docker-Compose` 사용 가능<br>무료 플랜에서는 도커 레이어 캐싱 불가|
|`Travis CI`|오픈소스는 무료<br>기업용 비싸 ㅠ,ㅠ 심지어 취미용까짘ㅋㅋㅋㅋㅋ|`Github` 의존도 높음 <br>빌드 매트릭스 제공|



