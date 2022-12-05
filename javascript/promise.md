## `Promise` `추가 2022/12/05`
> [참고자료](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- 프로미스가 생성된 시점에는 알려지지 않았을 수도 있는 값을 위한 **대리자**
- ✔ 미래의 어떤 시점에 결과를 제공하겠다는 약속(프로미스) 반환
- 프로미스 상태
  - 대기 `pending`: 이행하지도, 거부하지도 않은 초기 상태
  - 이행 `fulfilled`: 연산이 성공적으로 완료
  - 거부 `rejected`: 연산에 실패 
- ![image](https://user-images.githubusercontent.com/61215550/205526433-49175b98-76c3-40c7-9e59-658e12bb6051.png)
