## Github Actions
> [참고자료](https://insight-bgh.tistory.com/473)
- Github 저장소 기반 소프트웨어 개발 Workflow 자동화 할 수 있는 도구
- 주요 개념 4가지✅
  - Workflow
  - Event
  - Job
  - Step
  - Action
  - Runner

### 사용 예시
> 백엔드 CI 
```yml
name: Backend CI

on:
  pull_request:
    branches:
      - main
      - develop
    paths:
      - backend/**
      - .github/** # Github Actions 작업을 위한 포함

jobs:
  build:
    runs-on: ubuntu-latest

    defaults:
      run:
        working-directory: ./backend

    steps:
      - uses: actions/checkout@v3

      - name: Set up JDK 11
        uses: actions/setup-java@v3
        with:
          java-version: "11"
          distribution: "temurin"

      - name: Grant execute permission for gradlew
        run: chmod +x gradlew

      - name: Build with Gradle
        run: ./gradlew build

      - name: Publish Unit Test Results
        uses: EnricoMi/publish-unit-test-result-action@v2
        if: always()
        with:
          junit_files: ${{ github.workspace }}/backend/build/test-results/**/*.xml
Footer
```
