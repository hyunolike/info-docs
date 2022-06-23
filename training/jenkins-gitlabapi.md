## 젠킨스 파이프라인(선언적 스크립트)로 깃랩 api 정보를 얻어오자
### 선수지식
- Jenkins pipeline
- Groovy
- GitLab API
- JsonSlurper - 직렬화 
  - `@NonCPS` >> 직렬화 유의사항

### 개발 순서
#### 1. 먼저 Gitlab API 스크립트 작성
- `groovy` 로 작성
```groovy
import groovy.json.JsonSlurperClassic

def artifactsUrl = "http://10.10.10.41:8001/api/v4/projects/31/repository/tags/${buildNumber}"
def artifactsObjectRaw = ["curl", "--request", "GET", "--header", "PRIVATE-TOKEN: HugPzjfsCx1pD6Y_Myo8", "${artifactsUrl}"].execute().text

@NonCPS ⭐직렬화 관련 - 함수에서만 안전 >> 해당 어노테이션이 존재하지 않아도 정상 작동 그래도 달아놓자
def test(artifactsObjectRaw){
    return new JsonSlurperClassic().parseText(artifactsObjectRaw)
}
```
- `GitLab API` - `JSON`
- ![image](https://user-images.githubusercontent.com/61215550/175204078-349ccf82-a2ae-4a87-aca5-7e7cba3b208e.png)


#### 2. 선언적 파이프라인 코드 작성
```groovy
pipeline {
    agent any
    tools{
        jdk "jdk8"
        gradle "gradle"
    }
    environment{
        GIT_URL = "http://[설치된 깃랩 ip]:[포트]/root/mona-udm.git"
        PROJECT_NAME = "..._service"
    }
    stages{
        stage('Git Checkout') {
            steps{
                echo "--------git checkout step--------"
                checkout([$class: 'GitSCM', branches: [[name: 'refs/tags/${buildNumber}']], extensions: [], userRemoteConfigs: [[credentialsId: 'root', url: GIT_URL]]])
                script{
                    artifactsObject = test("${artifactsObjectRaw}")
                    
                    buildName("${artifactsObject.name}_${artifactsObject.commit.short_id}")
                    buildDescription("<table><tr><td style='padding: 5px;'>${PROJECT_NAME}</td><td></td></tr><tr><td style='padding: 5px;'><strong>Version</strong></td><td style='padding: 5px;'>${buildNumber}</td></tr><tr><td style='padding: 5px;'><strong>Git Commit</strong></td><td style='padding: 5px;'>${artifactsObject.commit.id}</td></tr><tr><td style='padding: 5px;'><strong>Release message</strong></td><td style='padding: 5px;'>${artifactsObject.commit.title}</td></tr><tr><td style='padding: 5px;'><strong>Author</strong></td><td style='padding: 5px;'>${artifactsObject.commit.committer_email}</td></tr></table>")
                }
            }
        }
    }
}
```

#### 3. 전체 코드
```groovy
import groovy.json.JsonSlurperClassic

def artifactsUrl = "http://10.10.10.41:8001/api/v4/projects/31/repository/tags/${buildNumber}"
def artifactsObjectRaw = ["curl", "--request", "GET", "--header", "PRIVATE-TOKEN: HugPzjfsCx1pD6Y_Myo8", "${artifactsUrl}"].execute().text

@NonCPS ⭐직렬화 관련 - 함수에서만 안전 >> 해당 어노테이션이 존재하지 않아도 정상 작동 그래도 달아놓자
def test(artifactsObjectRaw){
    return new JsonSlurperClassic().parseText(artifactsObjectRaw)
}

pipeline {
    agent any
    tools{
        jdk "jdk8"
        gradle "gradle"
    }
    environment{
        GIT_URL = "http://[설치된 깃랩 ip]:[포트]/root/mona-udm.git"
        PROJECT_NAME = "..._service"
    }
    stages{
        stage('Git Checkout') {
            steps{
                echo "--------git checkout step--------"
                checkout([$class: 'GitSCM', branches: [[name: 'refs/tags/${buildNumber}']], extensions: [], userRemoteConfigs: [[credentialsId: 'root', url: GIT_URL]]])
                script{
                    artifactsObject = test("${artifactsObjectRaw}")
                    
                    buildName("${artifactsObject.name}_${artifactsObject.commit.short_id}")
                    buildDescription("<table><tr><td style='padding: 5px;'>${PROJECT_NAME}</td><td></td></tr><tr><td style='padding: 5px;'><strong>Version</strong></td><td style='padding: 5px;'>${buildNumber}</td></tr><tr><td style='padding: 5px;'><strong>Git Commit</strong></td><td style='padding: 5px;'>${artifactsObject.commit.id}</td></tr><tr><td style='padding: 5px;'><strong>Release message</strong></td><td style='padding: 5px;'>${artifactsObject.commit.title}</td></tr><tr><td style='padding: 5px;'><strong>Author</strong></td><td style='padding: 5px;'>${artifactsObject.commit.committer_email}</td></tr></table>")
                }
            }
        }
    }
}
```
