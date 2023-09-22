## `viewport` 사용
> [참고자료](https://jongmin92.github.io/2017/02/09/HTML/viewport/)
- ⭐모바일 친화적
  - 모바일 > 사용자 이용 편의성 !!
### viewport
#### 정의
- viewport > 가상 윈도우 상 페이지 렌더링
- 😀즉, 화면 상의 `표시 영역`
- 모바일 사파리 > `viewport meta` 태그 도입 > 웹 페이지 개발자들 > 뷰포트 크기와 스케일 조정 가능!
- 웹 표준 아니지만 대부분 모바일 브라우저 지원!
#### 차이
- 데스크탑의 뷰포트
  - 브라우저 창의 뷰포트와 같음
  - 사용자 > 브라우저 크기 조절 가능
  - 스크롤 하여 나머지 영역 확인 가능
- 모바일 뷰포트
  - 더블탭, 줌인, 줌아웃 이용 > 뷰포트 배율 변경 (크키 아니야!)
 #### 중요한 이유
 - 모바일 브라우저 > 웹 페이지를 브라우징 하느 특징
 - ⭐스마트폰 브라우저 > 데스크탑 환경처럼 웹 페이지 전체 자연스럽게 브라우징 하는 `풀브라우징` 지원
#### 사용 방법
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
### viewport 속성
|속성 명| 설명|
|--|--|
|`width`|viewport 가로 크기 조정 / 일반적 숫자 가능 <br> `device-width`와 같은 특정 값 사용 가능|
|`height`|viewport 높이 크기 조정|
|`initial-scale`|페이지 처음 로딩 > 줌 레벨 조정 <br> 값 1일 경우 css 픽셀과 기기 종속적인 픽셀 간 1:1 관계 형성|
|`minimum-scale`|viewport 최소 배율값 / 기본값 `0.25`|
|`maximum-scale`|viewport 최대 배율값 / 기본값 `1.6`|
|`user-scalable`|사용자 확대/축소 기능 설정 > 기본값 `yes`|

### 🔥주의 사항 
- contents 보다 작은 `viewport` width/height 설정 무시
