## `Github Action CI/CD`]
> [공식 문서](https://docs.github.com/en/actions)<br>
> [참고 자료](https://velog.io/@youngerjesus/Github-Action%EC%9D%84-%EC%9D%B4%EC%9A%A9%ED%95%9C-CICD-%EA%B0%9C%EB%B0%9C-%EC%A3%BC%EA%B8%B0-%EC%9E%90%EB%8F%99%ED%99%94)
- ![](https://velog.velcdn.com/images%2Fyoungerjesus%2Fpost%2Feb950d02-73d3-4944-875a-37573d96dd97%2F%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-03-26%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%203.04.20.png)
### `CI(Continuous integration)`
- 지속적인 통합 >> 자동화 프로세스
- 코드 작성 > 빌드 > 테스트를 짧은 주기로 자동화
- 새로운 코드 변경 사항 >> 정기적으로 빌드 및 테스트되서 공유 레포 통합되기에 >> 여러 명의 개발자가 동시에 애플리케이션 개발과 관련된 코드 작업을 할 경우 충돌하는 문제 해결

### `CD(Continuous Delivery, Continuous Deployment)`
- 실제 개발(개발환경, 운영환경) ⭐
  - 개발 환경: Delivery + Deployment >> 자동화
  - 운영 환경: Delivery(수동화) + Deployment(자동화)

### Github Action
> [참고 자료](https://velog.io/@adam2/Github%EC%97%90-Action%EC%9D%B4%EB%9D%BC%EB%8A%94-%ED%83%AD%EC%9D%B4-%EC%83%9D%EA%B2%BC%EB%8B%A4..-github-Action%EC%9D%B4%EB%9E%80-3gk336pk8q)
-  CI/CD 가능하게 해주는 툴
#### 1. Workflow
- CI/CD 자동화된 프로세스 만들기 위한 `Yaml` 파일
- `workflow > job > step > action` 순
- 트리거 방식 ✔
  - `Schedule` 설정해 정해진 시간에 실행되도록
  - main 브랜치에 코드가 푸쉬되거나 어떤 브랜치 pull request 만들어지면 실행되도록
  - `webhook` 이용해 외부 이벤트에 대한 응답으로 실행되도록

|프로세스 절차|설명|
|--------------|------|
|`workflows`|- 레포에 정의한 자동화된 프로세스 절차<br>- 하나 이상의 Jobs로 구성, 이벤트 기반 트리거|
|`Jobs`|- 하나 이상의 steps로 구성 / workflows에 있는 Jobs끼리 병렬적으로 실행|
|`Steps`|- 하나의 task / 하나의 Jobs에 여러 task 넣을 수 있음<br>- step은 action, shell command로도 생성 가능<br>- 하나의 Job에 있는 step은 같은 runner에 의해 실행|
|`Actions`|- workflow에서 가장 작은 개념 / actions >> 독립적으로 실행할 명령|
|`Runners`|- Github에 의해 호스팅 되고있는 서버 >> `runner` 통해서 Job 실행시킨다고 생각하면 됨|

- ![image](https://user-images.githubusercontent.com/61215550/175226855-48d86302-7f74-4ad0-b8cd-89721b17ba4b.png)

