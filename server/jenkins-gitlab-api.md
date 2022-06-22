## `Jenkins` + `GitLab API` 
> [GitLab API](https://docs.gitlab.com/ee/api/) <br>
> [그루비 작성관련 자료](https://medium.com/@rijoalvi/jenkins-dynamic-parameters-using-extended-choice-parameter-plugin-and-groovy-1a6ffc41063f) <br>
> [GitLab API 작성 관련 자료](https://www.jacobbaek.com/860)
### 1. GitLab API를 통해 정보 가져오기 - 선행 작업
  - GitLab API는 공식 홈페이지 또는 따로 깃랩 서버 구축한 ip 또한 사용 가능! ✔
  - gitlab access token 새로 생성(api 선택)
  - groovy 작성
- [깃랩 api - 태그 관련 문서](https://docs.gitlab.com/ee/api/tags.html)
```groovy
import groovy.json.JsonSlurper

class test {
    static void main(String[] args) {
        List<String> artifacts = new ArrayList<String>()
        def artifactsUrl = "http://10.10.10.41:8001/api/v4/projects/31/repository/tags" ⭐ 여기서 31은 프로젝트 id >> gitlab api를 통해 프로젝트 정보를 파악하면 됨!!!
        def artifactsObjectRaw = ["curl", "--request", "GET", "--header", "PRIVATE-TOKEN: HugPzjfsCx1pD6Y_Myo8", "${artifactsUrl}"].execute().text

        printf('------------------\n')
        printf(artifactsObjectRaw + '\n')
        printf('------------------\n')

        def jsonSlurper = new JsonSlurper()
        def artifactsJsonObject = jsonSlurper.parseText(artifactsObjectRaw)
        def dataArray = artifactsJsonObject.name

        for(item in dataArray){
            artifacts.add(item)
        }
        print(artifacts)
    }
}
```

### 2. `Extended Choice Parameter Plugin` 이용해 그루브 스크립트 작성
```groovy
import groovy.json.JsonSlurper

List<String> artifacts = new ArrayList<String>()
def artifactsUrl = "http://10.10.10.41:8001/api/v4/projects/31/repository/tags"
def artifactsObjectRaw = ["curl", "--request", "GET", "--header", "PRIVATE-TOKEN: 1234", "${artifactsUrl}"].execute().text

def jsonSlurper = new JsonSlurper()
def artifactsJsonObject = jsonSlurper.parseText(artifactsObjectRaw)
def dataArray = artifactsJsonObject.name

for(item in dataArray){
    artifacts.add(item)
}
return artifacts.sort() ⭐
```
- 결과 화면
  - ![image](https://user-images.githubusercontent.com/61215550/174943433-6c22892b-5c37-4a72-9dbe-2df2351217fd.png)

### 3. 이제 해당 선택한 태그만을 가져와서 깃 소스코드를 가져오자
> [참고 자료](https://www.jenkins.io/doc/pipeline/steps/workflow-scm-step/#checkout-check-out-from-version-control)
- ⭐ `refs/tags/${buildNumber}` >> 해당 태그의 커밋을 가져오는 것!
- ![image](https://user-images.githubusercontent.com/61215550/174949737-ac944140-cc82-4b84-b0bc-5855193dd27c.png)

```groovy
checkout([$class: 'GitSCM', branches: [[name: 'refs/tags/${buildNumber}']], extensions: [], userRemoteConfigs: [[credentialsId: 'root', url: GIT_URL]]])
```
