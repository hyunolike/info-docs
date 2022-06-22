## `Jenkins` + `GitLab API` 
> [GitLab API](https://docs.gitlab.com/ee/api/) <br>
> [그루비 작성관련 자료](https://medium.com/@rijoalvi/jenkins-dynamic-parameters-using-extended-choice-parameter-plugin-and-groovy-1a6ffc41063f) <br>
> [GitLab API 작성 관련 자료](https://www.jacobbaek.com/860)
### 1. GitLab API를 통해 정보 가져오기 - 선행 작업
  - gitlab access token 새로 생성(api 선택)
  - groovy 작성
```groovy
import groovy.json.JsonSlurper

class test {
    static void main(String[] args) {
        List<String> artifacts = new ArrayList<String>()
        def artifactsUrl = "http://10.10.10.41:8001/api/v4/projects/31/repository/tags"
        def artifactsObjectRaw = ["curl", "--request", "GET", "--header", "PRIVATE-TOKEN: 1234", "${artifactsUrl}"].execute().text

        printf('------------------')
        printf(artifactsObjectRaw)
        printf('------------------')

        def jsonSlurper = new JsonSlurper()
        def artifactsJsonObject = jsonSlurper.parseText(artifactsObjectRaw)
        def dataArray = artifactsJsonObject.name

        for(item in dataArray){
            artifacts.add(item)
            print(artifacts)
        }
    }
}
```
