## MVVM 패턴
> [참고 자료](https://beomy.tistory.com/43)
- ![image](https://user-images.githubusercontent.com/61215550/176059116-96092b90-6a00-482d-af9c-f378e9ad543d.png)
- UI 및 UI 코드 분리하기 위한 `UI 아키텍처 디자인 패턴` ⭐
- Model + View + View Model
  - `Model`: 애플리케이션 사용되는 데이터와 데이터 처리하는 부분
  - `View`: 사용자에서 보여지는 UI 부분
  - `View Model`: View 표현하기 위해 만든 View를 위한 Model. / View 나타내주기 위한 Model이자 View를 나타내기 위한 데이터 처리하는 부분

### 1. 동작
1. 사용자 action들 >> view 
2. view + action >> `Command` 패턴 >> action들 >> View Model
3. View Model이 Model에게 데이터 요청
4. Model은 View Model에게 요청받은 데이터 응답 
5. View Model은 응답 받은 데이터 가공하여 저장
6. View는 View Model + Data Binding >> 화면 나타냄

### 2.특징
- `Command` 패턴 + `Data Binding` 패턴 으로 구현
  -  View <---> View Model 사이의 의존성 제거
-  View Model 1 : n View
- 장점 
  -  View <---> View Model 사이의 의존성 없음! (위 2가지 패턴 때문에!!)
  -  각각 부분 독립적 >> 모듈화하여 개발 가능 
-  단점
  -  View Mdoel의 설계 쉽지 않음

### (추가) `Command Pattern`
- 요청 >> 객체의 형태(캡슐화)
  - 사용자가 보낸 요청 재사용 ✔
- 매서드 이름, 매개변수 등 요청에 필요한 정보 저장 또는 로깅, 취소 패턴

### (추가) `Data Binding` 
> [참고 자료](https://docs.microsoft.com/ko-kr/windows/uwp/data-binding/data-binding-in-depth)
- UI에서 데이터 표시 + 선택적으로 해당 데이터와 동기화된 상태 유지하는 하나의 방법
- 데이터 문제 >> UI 문제와 분리 
  - 개념 간소화
  - 앱의 가독성, 테스트 용이성 및 유지 관리성 향상
- 제공자와 소비자로부터 데이터 소스 함께 묶어 동기화하는 일반적인 기법
  - xml 데이터 바인딩 + ui 데이터 바인딩

#### 왜 데이터 바인딩 사용?
- findViewId() 호출 x >> 자동으로 xml에 있는 view들 만들어줌
- data가 바뀌면 view 변경 하게 끔
- xml 리소스만 보고도 view에 어떤 데이터 들어가는지 파악 가능 
- 코드 가독성 및 코드량 감소
- `MVP` `MVVM` 패턵 구현하기위해 유용하게 사용 ⭐
- 데이터 바인딩 단독보다는 위의 아키텍처와 함께 사용하는 것이 빛을 발한다는 업계의 오피셜
