## 프론트 자주 쓰이는 패턴
- ![image](https://user-images.githubusercontent.com/61215550/214762837-e60de0f4-6634-44c4-aff7-22ec5c4dcc0d.png)

### 복잡한 뷰 많아짐
- 카카오맵, 구글 웹엑셀
- 프론트엔드 자체 뷰
- ⭐ 프론트엔드의 뷰 >> 사건의 발생지 / 온갖 이벤트 발생
  - 사용자 입력값
  - 화면 선택, 변경
  - 스케줄(setTimeout ... )
  - 서버와 통신
  - ...

### 뷰 모델간 복잡도 증가 ㅠ,ㅠ
|뷰|모델|뷰 모델|
|![image](https://user-images.githubusercontent.com/61215550/214763045-8992a8de-46a4-4d92-8afe-405450853b8c.png)|![image](https://user-images.githubusercontent.com/61215550/214763067-8b60509d-bced-497a-a653-0dbf17997955.png)|![image](https://user-images.githubusercontent.com/61215550/214763116-f1802279-5d1f-438d-a14e-24d4f046956c.png)|

### 컨트롤러 두기
- ![image](https://user-images.githubusercontent.com/61215550/214763215-579a13fe-4396-4e2d-9b45-d8ea4f90bec2.png)

### 뷰 >> 계층적인 구조
- 잦은 `re-rendering` >> dom 을 바꾸는 것
- 제어하기 위한 원래 구조(dom 구조)

### ✔ 정리
- ![image](https://user-images.githubusercontent.com/61215550/214763322-c8faaaf8-4c2a-426f-ae57-59ef8674fcfb.png)
- ⭐ 요즘 사용되는 기술
  - 데이터 바인딩 (뷰, 모델 바인딩)
  - MVVM >> 뷰에서 쓰는 모델 가지고 있다가 변경사항 하는거 
  - Flux 아키텍처 
