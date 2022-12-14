## 뷰 상태관리 - `vuex` / 중앙 집중식 저장소
> [참고자료](https://joshua1988.github.io/vue-camp/vuex/concept.html)
- 컴포넌트가 많아졌을 때, 컴포넌트 간의 데이터 전달이나 관리가 어렵기 때문
- ✔ **데이터 전달** 을 더 명시적! 효율적! 으로 하기 위한 방법 
- ![image](https://user-images.githubusercontent.com/61215550/207471447-c7284841-cc69-4433-9df6-0d1485ce2072.png)

|vuex|
|--|
|![image](https://user-images.githubusercontent.com/61215550/206086470-c2514925-376c-4442-9691-2e0cbbf080dc.png)|
|⭐화면(view) >> 화면에서의 이벤트 발생(Actions) >> 데이터 변경(State)의 단방향 데이터 흐름|
### 뷰엑스 기술 요소
> [참고자료](https://velog.io/@subin1224/Vuex-%EC%83%81%ED%83%9C%EA%B4%80%EB%A6%AC-%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AC)
#### `state`
> 💡 원본 소스의 역할을 하는 state
- `getter` 통해 접근! (직접적으로 접근도 가능)
- `mutation`을 통해 데이터 변경 가능! ✔
#### `getters`
> 💡자주 처리해야 하는 state의 데이터를 **캐시** 를 통해 코드의 반복 줄여줌!
- 속성 유형 접근
- 메소드 유형 접근
#### `mutations`
> 💡 Vuex 저장소에서 실제로 상태를 변경하는 유일한 방법!
- 실제 상태 수정 하는 곳!
- 페이로드를 가진 커밋
- 객체 스타일 커밋
- Vue의 반응성 규칙을 따르는 Mutations
#### `actions`
- Mutations과 유사
- 임의의 비동기 작업 포함 가능!
### 뷰엑스 구조도
> ⭐ 컴포넌트 > 비동기 로직 `Actions` > 동기 로직 `Mutation` > 상태
- ![image](https://user-images.githubusercontent.com/61215550/206087826-cd283343-d926-4041-80da-5df9dc885124.png)
---
### (추가) Vue에서의 데이터 전달 방법 😛
> [참고자료](https://velog.io/@subin1224/Vuex-%EC%83%81%ED%83%9C%EA%B4%80%EB%A6%AC-%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AC)


|`Props` & `Emit`|`Provide` & `Inject`|`Vuex`|
|--|--|--|
|![image](https://user-images.githubusercontent.com/61215550/206087133-152081aa-c2dc-40c7-bfb6-8566eddd78ca.png)|![image](https://user-images.githubusercontent.com/61215550/206087148-a89c3534-bf5f-4c77-ac81-f7ecf4c25f34.png)|![image](https://user-images.githubusercontent.com/61215550/206087178-4e68bc01-1e2a-4a23-ab70-11bb3e5cd0e1.png)|
