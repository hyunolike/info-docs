## 젠킨스 스크립트(파이프라인)
> [참고자료](https://velog.io/@revelation/Jenkins-pipeline-%EC%82%AC%EC%9A%A9%ED%95%B4%EB%B3%B4%EA%B8%B0)
- jenkins pipeline >> 젠킨스의 플러그인들 중 하나
  - 연속적인 이벤트 / job의 그룹 실행 가능 >> 하나의 job에서 여러 가지 일들 할 수 있게 도와줌

### 1. Pipeline Concept
- Pipeline
- Agent/Node
- Stage
- Step

#### 1-1. 작성
- pipeline 전용 DSL로 작성된 스크립트 코드 작성
- Jenkinsfile 이라는 곳에다가 DSL 문법으로 뭔가 작성 

### 2. 파이프라인 생성 방법
- 크게 3가지
  - WEB UI
  - SCM (EX. github에 jenkins 파일 만들어 땡겨서 관리 및 젠킨스 실행
  - Blueocean 플러그인 이용
#### 2-1. 2가지 타입 작성 가능
- 모두 `Groovy` 언어
  - `Declarative Pipeline`: 쉽게 작성 가능 
  - `Scripted Pipeline`: 위에꺼보다 효과적이고 많은 기능 포함해서 작성 가능 >> 어려움
### 3. Scripted Pipeline
#### 3-1. 지시어 `Directive`
- `node`: 마스터가 관리하는 서버 / 프로그램 
- `dir`: 명령 수행할 디렉토리(폴더) 정의
- `stage`: 파이프라인 각 단계
- `git`: git 원격 저장소 프로젝트 clone
- `def`: groovy 변수



```groovy
pipeline {
    agent any
    
    stages() {
        stage('git clone') {
            steps() {
                git 'https://github.com/leeseok0916/jenkinsTest.git'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        
        stage('execute sh') {
            steps {
                sh "chmod 774 ./project.sh"
                sh "./project.sh"
            }
        }        
    }
}

혹은
node {
    stage('git clone') {
        git 'https://github.com/leeseok0916/jenkinsTest.git'
    }
    stage('Test') {
        echo 'Testing....'
    }
    stage('execute sh') {
		sh "chmod 774 ./project.sh"
        sh "./project.sh"
    }
}
```
### 4. Flow Control 
- [참고자료](https://www.jenkins.io/doc/book/pipeline/syntax/#flow-control)
