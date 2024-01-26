## 미디어쿼리 - 데스크탑 퍼스트, 모바일 퍼스트
> [참고자료](https://uxkm.io/publishing/css/03-cssMiddleclass/09-css_media_part2#gsc.tab=0)
### 1.⭐모바일 퍼스트 디자인
- 구축 단계부터 `모바일 중심` 구축


```css
/* Mobile style */

/* Custom, iPhone Retina : 320px ~ */
@media only screen and (min-width : 320px) { … }

/* Extra Small Devices, Phones : 480px ~ */
@media only screen and (min-width : 480px) { … }

/* Small Devices, Tablets : 768px ~ */
@media only screen and (min-width : 768px) { … }

/* Medium Devices, Desktops : 992px ~ */
@media only screen and (min-width : 992px) { … }

/* Large Devices, Wide Screens : 1200px ~ */
@media only screen and (min-width : 1200px) { … }
```
#### 1-1. 모바일 퍼스트 디자인 이유
1. 모바일 앱에서 데스크톱 확장 쉬움 / 데스크탑에서 모바일 어려움 ㅠ,ㅠ
2. 모바일 > 데스크톱에 비해 제공 가능 정보의 양 적음
3. 데스크톱 기준 > 빽빽하게 작성된 웹 사이트 > 모바일 옮기는 기획부터 고려하여 작업
4. 반대로, 모바일 기준! `느슨`하게 작성된 웹 페이지 > 데스크톱 충분히 쉽게 옮길수 있음
### 추가
- 우리나라 > 데스크톱 우선주의 `Desktop First`
- 해외 > 모바일 우선주의 `Mobile First`
### 2. 데스크톱 퍼스트가 모바일 퍼스트에 비해 가질수 있는 장점과 단점
- 장점
  - 확실한 구버전 ie대응
  - 익숙한 작업 순서 유지
  - 리뉴얼 없는 모바일 대응 추가
- 단점
  - 오버라이딩(속성 덮어쓰기)의 발생빈도가 높아짐
  - 사이드 이펙트(수정시 의도하지 않게 발생하는 부작용) 문제
 


