## Jenkins - SSH 
> [참고 자료](https://royleej9.tistory.com/m/entry/Jenkins-SSH-%EC%82%AC%EC%9A%A9-pipeline-SSH-Agent)
- 작업 순서
  1. `SSH Agent` 플러그인 설치
  2. SSH 인증서 생성
  3. Jenkins에 ssh 인증 정보 등록
  4. pipeline에서 ssh 사용

### 2. SSH 인증서 생성 ⭐
- `ssh-keygen -t rsa -f [경로/파일명]`

### 3. Jenkins에 ssh 인증 정보 등록
```
Kind : SSH Username with private key
ID : 중복되지 않는 인증 ID - 해당 ID 값으로 pipline에서 인증 정보를 사용
username : 생략
private key : ssh-keygen 으로 생성한 private key 내용 (ex: jenkins_rsa)  
              cat jenkins_rsa 명령어로 출력되는 내용
passphrase : ssh-keygen으로 인증키 생성시 입력한 password
```

### 4. pipeline에서 ssh 사용
```
pipeline {
    agent any
    stages {
        stage('test ssh') {
            steps {        
                sshagent (credentials: ['jenkins-ssh']) {
                sh """
                    ssh -o StrictHostKeyChecking=no ${TARGET_HOST} "pwd"
                """
                }
            }
        }

        stage('multiline ssh') {
            steps {        
                sshagent (credentials: ['jenkins-ssh']) {
                sh """
                    ssh -o StrictHostKeyChecking=no ${TARGET_HOST} '
                    rm -rf test
                    mkdir test
                    cd test
                    mkdir test2
                    cd test2
                    pwd
                    '
                """
                }
            }
        }
    }
    environment {
        TARGET_HOST = "test@192.168.0.7"
    }
}
```
