## [AWS] Lambda
> [참고 자료](https://seoyeonhwng.medium.com/aws-lambda%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80-44df535d5487)

![image](https://user-images.githubusercontent.com/61215550/162564279-a70553e8-1bb7-4f2f-b4a7-bd4b446a4579.png)
### 람다??
- 서버리스 컴퓨팅 플랫폼
  - 서버리스: 서버가 없다는 뜻이 아니고, 서버의 존재를 신경쓸 필요가 없다라는 뜻 / 사용자는 오직 코드에만 집중 가능!
- 사용한 컴퓨팅 시간, 용량에 대해 비용 지불

### 언제 사용할까
- 코드를 계속 실행시키 보다는 특정한 시기에만 실행시키는 경우
  - 서버 띄우지 않고 간단한 코드 실행시키고 싶은 경우
  - 특정 기간 또는 특정 주기로 코드 실행시켜야 하는 경우 
  - 트리거가 실행될때만 코드 실행시키고 싶은 경우

### 람다에 코드 올리는 방법 3가지
1. 인라인 코드
2. zip 파일 업로드
3. 아마존 s3에서 파일 업로드

### `Serverless Model`
- 서버가 없다는 뜻 아니고, 사용자가 직접 관리해야 하는 서버가 없다! 
![image](https://user-images.githubusercontent.com/61215550/162564204-a4a2c23e-a9dc-4bda-9611-938f8adef78b.png)

- 보이지 않는 곳에서 관리형 서버(추상화된 서버) >> 필요에 따라 `Scale up` / `Scale down` ✔
- 특정한 요청(이벤트)의 트리거 발생 >> 함수 호출
