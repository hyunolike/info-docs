## CI CD
> [참고자료](https://techblog.woowahan.com/2579/)
- CI(Continuous Integration) ✔ 통합을 지속적으로 수행
  - `build` `test` 실시하는 프로세스 / 이러한 통합 프로세스를 상시 해주는 것
- CD(Continuous Delivery or Continuous Deploy) ✔ 짧은 주기로 개발중인 소프트웨어 배포, 그 과정 자동화
  - 짧은 주기로 소프트웨어 개발하는 소프트웨어 공학적 접근의 하나
  - 소프트웨어가 언제든지 신뢰 가능한 수준으로 출시될 수 있도록 보증
- Jenkins 😛
  - 무료 사용
  - 사용자 정의 옵션
  - 방대한 양의 플러그인
  - 다양한 적용사례 및 풍부한 레퍼런스
  - Remote access API 제공
- 도커 😛
  - 젠킨스 서버 띄우기 위해 여러가지의 서버 설정 등과 설치가 필요 >> 이 모든 일련의 과정을 Dockerfile 에 작성하고 운영에 오는 리소스 줄일수 있음
### 구조
- ![image](https://user-images.githubusercontent.com/61215550/204166879-9d39e44d-2b4d-47a2-83da-22c9412d3c5b.png)
