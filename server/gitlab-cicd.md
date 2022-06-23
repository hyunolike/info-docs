## `GitLab CI/CD` - GitLab runner
- 깃랩: 온프레미스 설치형 깃 호스팅 / 웹서비스 형
- 깃허브: 웹서비스 형태
- ![image](https://user-images.githubusercontent.com/61215550/175231399-54846c57-33f7-423d-9f1d-805366696387.png)

### GitLab runner 
> [참고 자료](https://europani.github.io/git/2021/07/20/010-gitlab-runner.html)
- 젠킨스와 같은 설치형 ✔
- 서버에 직접 설치
### 순서
1. gitlab-runner 설치
2. runner 등록
3. gitlab 사이트에서 runner 등록 확인
  - `GitLab > project > Settings > CI/CD > Runners`
4. `gitlab-ci.yml` 작성
```yml
deploy-to-develop:
  stage: deploy
  only:
    - develop
  variables:
    GIT_STRATEGY: clone
    PROJECT_PATH: /usr/local/mypro
  script:
    - whoami
    - cd $PROJECT_PATH
    - git pull
    - docker-compose up -d --build
    - echo "Deployed To Develop Server"
  tags:           # runner 등록 4번 과정의 tag와 맵핑된다
    - develop
    
deploy-to-production:
  stage: deploy
  only:
    - master
  variables:
    GIT_STRATEGY: clone
    PROJECT_PATH: /usr/local/mypro
  script:
    - whoami
    - cd $PROJECT_PATH
    - git pull
    - docker-compose up -d --build
    - echo "Deployed To Production Server"
  tags:           # runner 등록 4번 과정의 tag와 맵핑된다
    - master
```
