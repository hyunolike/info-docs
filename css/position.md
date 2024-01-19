## `position` 속성
> [참고자료](https://seokzin.tistory.com/entry/CSS-position-%EC%86%8D%EC%84%B1-static-relative-absolute-fixed-sticky?category=695592)
- 기본 개념
  - `display`: 요소가 차지할 영역
  - `position`: 요소가 배치할 영역
### 1. static
- 기본값
- 일반적인 문서의 흐름에 따라 화면 배치
- 좌표값(top, bottom, left, right) & `z-index` 설정 무시
### 2. relative
- 원래 위치를 기준으로 좌표 값만큼 `이동`
### 3. absolute
- 상위 요소 중 static 아닌 첫 요소 기준으로 좌표 값 만큼 이동
### 4. fix
- 부모 관계 없이 브라우저의 `viewport` 기준으로 좌표 값 이동
### 5. sticky
- 평소 static 처럼 보이다가 > `특정 스크롤 지점` 도달 > `fixed` 처럼 변함!
