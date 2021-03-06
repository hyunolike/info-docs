## Jenkinsfile
> [참고 자료](https://bob-full.tistory.com/10)
- 크게 3가지 존재 ✔
  - `Job` 구성을 통해 __Jenkinsfile__ 작성
  - `SCM` 이용해 Jenkinsfile 작성 >> __github__ 에서 관리 후 젠킨스에서 실행
  - `Blueocean` 플러그인으로 UI 통해 __Jenkinsfile__ 작성 >> github 관리
### 1. Jenkinsfile 작성 
> [참고 자료](https://www.jenkins.io/doc/book/pipeline/syntax/)
- 작성 유형 2가지 존재 ✔ >> ⭐ 2가지 동시 사용 불가
  - `Declarative Pipeline`: 보다 쉽게 작성 할 수 있게 커스텀. - `Groovy-syntax`기반 / Groovy 문법 몰라도 작성 가능
  - `Script Pipeline`: Groovy 기반, Declarative보다 효과적으로 많은 기능 포함해 작성 가능  

#### 1.1 `Declarative`
```
pipeline {
    agent none
    stages{
        stage('Parallel Test') {
            parallel { 
                stage('Build-test-1') {
                    steps{ build 'Build-test-1' }
                }
                stage('Build-test-2') {
                    steps{ build 'Build-test-2' }
                }
                stage('Build-test-3') {
                    steps{ build 'Build-test-3' }
                }
            }
        }
        stage('Build-test-4') {
            steps{
                build 'Build-test-4'
            }
        }
    }
}
```
#### 1.2 `Scripted`
```
node {
  stage('Parallel-test') {
      parallel 'Build-test-1' : {
          build job : 'Build-test-1'
      } , 'Build-test-2' : {
          build job : 'Build-test-2'
      } , 'Build-test-3' : {
          build job : 'Build-test-3'
      }
  }
  stage('Build-test-4') {
     build job : 'Build-test-4'
  }
}
```

### 2. `2가지` 작성 유형 차이
- ✔ Jenkins Pipeline >> Groovy 기반 / Jenkins Pipeline의 구현자 >> Groovy - Scripted Pipeline DSL
- 2가지 모두 동일한 파이프라인 하위 시스템
- `Declarative`
  - 더 간단하고 더 독단적인 구문 제공
  - 보다 엄격하고 미리 정의된 구조로 사용자의 사용 제한 >> 더 간단한 연속 전달 파이프라인
- `Scripted`
  - 요구사항이 더 복잡한 사용자에게 이상적인 선택
