## PUT vs PATCH
> [참고자료](https://velog.io/@vagabondms/%EA%B8%B0%EC%88%A0-%EC%8A%A4%ED%84%B0%EB%94%94-PUT%EA%B3%BC-PATCH-%EC%B0%A8%EC%9D%B4)
- 2개 모두 업데이트 기능

### 개념 비교
|PUT|PATCH|
|------|------|
|요청 페이로드를 사용해 새로운 리소스 **생성** 및 대상 리소스를 나타내는 데이터 **대체**|리소스의 **부분적인 수정**을 할 때 사용|
|![image](https://user-images.githubusercontent.com/61215550/196564597-989ac4fe-8812-4a1d-9591-9aa9f979657f.png)|![image](https://user-images.githubusercontent.com/61215550/196564614-2385356e-72db-4391-84fc-f7bbe23e2afe.png)|
|![image](https://user-images.githubusercontent.com/61215550/196564672-52cdd6da-1227-4853-b616-da13588960ce.png)|![image](https://user-images.githubusercontent.com/61215550/196564693-55b7d282-d3bd-4bc5-8e0a-2c9c15d1f276.png)|

### ⭐멱등성
- 동일한 요청을 한 번 보내는 것과 여러 번 연속으로 보내는 것이 **같은 효과** 지님 서버의 상태도 동일하게 남을 때, 해당 HTTP 메서드가 멱등성을 가졌다고 함!
- PUT: 멱등성 ⭕ `리소스의 모든 것을 업데이트`
- PATCH: 멱등성 ❌ `리소스의 일부를 업데이트`
  - ![image](https://user-images.githubusercontent.com/61215550/196564957-72d16b16-7a07-4f80-9400-55072b28fb09.png)
   
