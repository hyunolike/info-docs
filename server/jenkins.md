## `Jenkins`
> 1개의 컴포넌트가 아닌 여러개의 컴포넌트 구성해서 자동화 배포하기 위해 사용
### 1. 젠킨스 작동 순서
1. 코드 가져오기
2. 빌드(환경)
3. 타겟 서버 설정 및 연결
4. 파일 옮기기 >> SSH 통신
5. `deploy` 연결
6. TEST 환경 >> 테스트는 작성된 테스트 코드가 아닌 실제 띄어진 api 테스트 하는 것 ✔ (개발자 커스텀)
8. `health check`

### 2. 젠킨스 스크립트 작성 ⭐ >> 환경 설정
> 젠킨스 파이프라인
- 크게 __2가지 방법__ 으로 나뉜다.
  1. 깃(SCM) 저장된 스크립트 가져와서 사용
  2. 직접 작성
- ![image](https://user-images.githubusercontent.com/61215550/171069408-241e8276-9de7-44f2-b265-4a0279b8afba.png)

#### 2-1. `Jenkinsfile` 기본 구성
```groovy
node {  
    stage('Build') { 
        // 
    }
    stage('Test') { 
        // 
    }
    stage('Deploy') { 
        // 
    }
}
```
- ![image](https://user-images.githubusercontent.com/61215550/171069436-b98f7fd6-e17a-4210-8385-dc572ad6c481.png)

#### 2-2. `Pipeline Script from SCM` 왜 사용?
- SCM(Source code management)로부터 지정된 위치의 script 불러와 실행 가능 >> 코드 관리 용이하고 보안성 측면에도 좋음

### 3. 알아두면 좋을 것
- 젠킨스 파일 작성 구성
- 방화벽 문제 발생
  - ![image](https://user-images.githubusercontent.com/61215550/171070918-9cbd77a0-ab85-4d11-b810-6d00b69a812c.png)

- 서버단 통신은 `SSH` 통신
  - `SSH(Secure Shell)` 통신: 인터넷 연결만 되어있어도 내 컴퓨터 활용해 다른 지역에 있는 컴퓨터 혹은 서버 관리할 수 있게 컴퓨터 간 통신을 돕는 프로토콜
