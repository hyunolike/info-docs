## 데이터처리 모델 - 동기 / 비동기
> [참고자료](https://velog.io/@slobber/%EB%8F%99%EA%B8%B0%EC%99%80-%EB%B9%84%EB%8F%99%EA%B8%B0%EC%9D%98-%EC%B0%A8%EC%9D%B4)
- 데이터 처리 모델 >> 데이터 받는 방식
### 1. 동기 📌추구하는 행위, 목적 동시 이뤄짐
- 한 개의 데이터 요청에 대한 서버의 응답이 이뤄질 떄까지 계속 대기
### 2. 비동기 📌추구하는 행위, 목적 다를수 있고 동시에 이뤄지지도 않아
- 동시에 일어나지 않는거
- 요청한 결과는 동시에 일어나지 않을거라는 약속
### 3. 장단점
> 동기(블록) 비동기(논블록)
- 동기 
  - 장점: 설계가 매우 간단 / 직관
  - 단점: 결과가 주어질 떄까지 아무것도 못하고 대기
- 비동기
  - 장점: 요청에 따른 결과가 반환되는 시간 동안 다른 작업 수행 가능
  - 단점: 동기식보다 설계가 복잡
