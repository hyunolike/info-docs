## 깃 브랜치 전략
> [참고 자료](https://hyeon9mak.github.io/git-branch-strategy/) <br>
> [Git flow, GitHub flow, GitLab flow](https://ujuc.github.io/2015/12/16/git-flow-github-flow-gitlab-flow/)
- 브랜치 전략: 여러 개발자가 하나의 저장소를 사용하는 환경에서 저장소를 효과적으로 활용하기 위한 `work-flow`
- 브랜치의 생성, 삭제, 병합 등 git의 유연한 구조를 활용해서 각 개발자들의 혼란을 최대한 줄이며 다양한 방식으로 소스를 관리하는 역할
- 브랜치 생성 규칙을 만들어 협업을 유연하게 하는 방법론
- 크게 2가지 존재
  - `Github-flow` 간단하고 민첩
  - `git-flow` 복잡하지만 체계적!
  - `Gitlab-flow` (추가)

### 1. `Github-flow`
1. 브랜치 생성
  - 브랜치 하나에 의존하기 때문에 
  - __브랜치 이름을__ 통해 의도를 명확하게 드러내는 것이 중요
2. 열심히 개발, 커밋!!!
  - 커밋 메시지에 의존하기 때문에, __커밋 메시지를__ 최대한 상세하게 적어주는 것이 중요
3. PR 생성
  - 개발이 완료되면 마스터 브랜치쪽으로 `pull-request`
4. 리뷰, 토의, 리뷰, 토의 무한 반복하자 
  - 충분한 리뷰와 토의를 거침
  - 곧장 배포하는 것과 다르지 않기 때문에 / 상세한 리뷰와 토의가 이뤄져야 한다. 
5. 토의가 끝났어도 테스트
  - 라이브 서버(혹은 테스트 환경)에 배포 !! 만약 문제 발생시 다시 배포하여 초기화
6. 최종 Merge
  - 문제 발생하지 않으면 그대로 마스터 브랜치에 푸시, 즉시 배포
  - 마스터 브랜치를 최신 브랜치로 가정하기 때문에 __배포 자동화 도구__ 이용해서 즉시 배포!

#### `Github-flow` 특징
- 브랜치 전략 단순, git 처음 접하는 사람도 쉽게 접근 가능
- `CI/CD` 자연스럽게 이뤄짐

### 2. `git-flow`
![image](https://user-images.githubusercontent.com/61215550/163916994-923fd80c-e2ff-4f94-9f19-5e706d870297.png)
- 5가지 브랜치 이용해서 저장소 운영하는 브랜치 전략
  - `master` `develop`: 메인 브랜치
  - `feature` `release` `hotfix`: 보조 브랜치(머지되면 사라져ㅠ,ㅠ)

### 어떤거 사용?
- `git-flow`
  - 1개월 이상의 긴 호흡으로 개발하여 주기적으로 배포, QA 및 테스트, hotfix 등 수행할 수 있는 여력이 있는 팀이라면 git-flow 적합
- `Github-flow`
  - 수시로 릴리즈 되어야 할 필요가 있는 서비스를 지속적으로 테스트하고 배포하는 팀!
  - 예시
  - ![image](https://user-images.githubusercontent.com/61215550/163916008-1633dd1a-0d6c-4098-afe0-c6d885ec4d88.png)

