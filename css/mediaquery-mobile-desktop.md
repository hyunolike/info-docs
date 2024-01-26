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
### 3. ⭐반응형 웹페이지 > 대부분의 레이아웃의 5가지 패턴 요약
1. `Mostyl Fluid` (유동형)
2. `Column Drop` (열 드롭)
3. `Layout Shifter` (레이아웃 시프터)
4. `Tiny Tweaks` (작은 변화)
5. `Off Canvas` (캔버스 오프)
#### 3-1. 유동형 - 가장 많이 사용되는 패턴
- 📌 레이아웃 그대로 유지
- 가장 작은 화면 > 수직으로 칼럼 세워
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/e5b26695-7e91-47d9-985a-90a845dee75f)

#### 3-2. 열 드롭
- 화면 작아짐에 따라 > 칼럼 아래로 떨어트려
- 칼럼폭 크기 달라져도 변함이 별도 없어
- 결국 모드 열이 수직으로 쌓여
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/ba10c0eb-72f5-4a20-8f4d-c12aa779ed55)

#### 3-3. 레이아웃 시프터
- 다양한 디바이스에 따라 각기 다른 레이아웃 보여주는 패턴
- 복잡하고 많은 작업 > 혁신적인 다자인 담을 수 있다!
- `여러개의 중단점` > 여러 스크린 너비에 민감하게 반응하는 패턴
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/e4870a43-6eb4-4a69-a994-4ad77b2ff007)

#### 3-4. 작은 변화
- 하나의 칼럼 사용하는 패턴
- 블로그 많이 사용
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/bc33c238-4629-49d0-bccf-bcc151b51263)

#### 3-5. 캔버스 오프
- 작은 화면에서는 메인 칼럼 하나
  - 다른 부가적인 것들은 화면 밖에 숨기는 패턴
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/7173a591-c776-4ac1-b9ff-64b3c423662c)
