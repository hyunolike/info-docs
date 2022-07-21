## Architecture Pattern
> [참고자료](https://www.geeksforgeeks.org/android-architecture-patterns/)
- 크게 3 종류
  - `MVC`
  - `MVP`
  - `MVVM`

### 각 패턴 로직 비교
|MVC|MVP|MVVM(권장)|
|-----|-----|----|
|![image](https://user-images.githubusercontent.com/61215550/180101184-af12881c-33f1-4c4d-9454-7c4593754f20.png)|![image](https://user-images.githubusercontent.com/61215550/180101877-cb397357-af02-4bc5-bf31-b8b339bc2ed2.png)|![image](https://user-images.githubusercontent.com/61215550/180111023-3259a365-b903-42a5-8ce2-335b8523e21b.png)|

### 1. MVC
|용어|설명|
|-----|---------|
|Model|- 데이터 저장 계층<br>- 도메인 논리(실제 비즈니스 규칙) 처리<br>- 데이터베이스 및 네트워크 계층과의 통신 담당|
|View|- UI 계층<br>- Model에 저장된 데이터의 시각화 제공|
|Controller|- 핵심 로직 포함하는 레이터<br>- 사용자의 행동에 대한 정보 얻고 필요에 따라 모델 업데이트|

#### 1.1 장점
- 코드 테스트 가능성 높이고 관심사 분리 지원 >> 새로운 기능 더 쉽게 구현 가능
- Model 및 Controller 의 단위 테스트는 Android 클래스 확장하거나 사용하지 않기에 가능
- View 단일 책임 원칙 준수한다면 UI 테스트를 통해 View의 기능을 확인 가능(데이터 로직 구현하지 않고 모델에서 컨트롤러 업데이트 및 데이터 표시)

#### 1.2 단점
- 코드 레이어 >> MVC 올바르게 적용되어도 서로 의존
- UI 로직 처리하는 매개변수 없음 >> 데이터 표시하는 방법 

### 2. MVP
> ✔ 동일한 설명 제외 / 추가적인 설명만 작성
|용어|설명|
|-----|-------|
|Model||
|Vieww|- 데이터 시각화 제공 및 Presenter에게 알리기 위해 사용자의 작업 추적|
|Presenter|- Model에서 데이터 가져오고 UI 논리 적용하여 표시할 항목 결정<br>- View 상태 관리 및 View에서 사용자의 입력 알림에 따라 조치 취함|

### 3. MVVM
> ✔ 동일한 설명 제외 / 추가적인 설명만 작성
- ⭐ AAC(Android Architecture Components) 출시 이후 >> 안드로이트 팀 이 아키텍처 패턴 권장
- `MVVM` `MVP` 둘다 __View__ 계층의 상태와 동작을 추상화하는데 효율적!!!

|용어|설명|
|-----|-------|
|Model|- 데이텃 소스 추상화 담당<br>- `Model` `ViewModel` 함께 작동하여 데이터 가져오고 저장|
|View|- `ViewModel` 사용자의 작업을 알리는 것|
|ViewModel|- `View`와 관련된 데이터 스트림 노출|

### 4. 각 아키텍처 비교\
|Pattern|Android API 종속성|xml 복잡성|단위 테스트 가능성|Follow Modular and single / responsibility principle|
|----------|--------------------|----------------------|-----------------------------------------------------|
|`MVC`|High|Low|Difficult|No|
|`MVP`|Low|Low|Good|Yes|
|`MVVM`|Low or No dependency|Medium to High|Best|Yes|
