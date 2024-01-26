## media query `updated by 2024/01/26` - 모바일 분기점 `768px` 
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/1de4efd0-cafc-4aa2-99bd-66af0c9aac2e)

### ⭐🔥 미디어 쿼리 템플릿
#### 1. Device 별 사이즈
```css

/* All Device */
@media screen {
  /* 모든 해상도를 위한 공통 코드를 작성한다. 모든 해상도에서 이 코드가 실행됨. */
}

/* Mobile Device */
@media all and (max-width:768px) {
  /*
  768px 미만 해상도의 모바일 기기를 위한 코드를 작성한다.
  모든 해상도에서 이 코드가 실행됨.
  미디어 쿼리를 지원하지 않는 모바일 기기를 위해 미디어 쿼리 구문을 사용하지 않는다.
  */
}

/* Tablet Device */
@media all and (min-width:768px) {
  /*
  사용자 해상도가 768px 이상일 때 이 코드가 실행됨.
  테블릿과 데스크톱의 공통 코드를 작성한다.
  */
}

/* Tablet & Desktop Device */
@media all and (min-width:768px) and (max-width:1024px) {
  /*
  사용자 해상도가 768px 이상이고 1024px 이하일 때 이 코드가 실행됨.
  아이패드 또는 비교적 작은 해상도의 랩탑이나 데스크톱에 대응하는 코드를 작성한다.
  */
}

/* Desktop Device */
@media all and (min-width:1025px) {
  /*
  사용자 해상도가 1025px 이상일 때 이 코드가 실행됨.
  1025px 이상의 랩탑 또는 데스크톱에 대응하는 코드를 작성한다.
  */
}
```
#### 2. Mobile First 반응형 웹
```css
/* All Device */

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
#### 3. Desktop Frist 반응형 웹
```css
/* All Device */

/* Large Devices, Wide Screens : ~ 1200px */
@media only screen and (max-width : 1200px) { … }

/* Medium Devices, Desktops : ~ 992px */
@media only screen and (max-width : 992px) { … }

/* Small Devices, Tablets : ~ 768px */
@media only screen and (max-width : 768px) { … }

/* Extra Small Devices, Phones : ~ 480px */
@media only screen and (max-width : 480px) { … }

/* Custom, iPhone Retina : ~ 320px */
@media only screen and (max-width : 320px) { … }
```

### 📡🔥단계별 반응형 개발 예시
![image](https://github.com/hyunolike/info-docs/assets/61215550/11169ace-1445-4280-85e7-da175c99e720)

### media query 기기별 해상도 분기점
> [참고자료](https://ifhead.tistory.com/entry/Web-%EB%AF%B8%EB%94%94%EC%96%B4-%EC%BF%BC%EB%A6%AC-%EA%B8%B0%EA%B8%B0%EB%B3%84-%ED%95%B4%EC%83%81%EB%8F%84-%EB%B6%84%EA%B8%B0%EC%A0%90)
- ⭐ 필수 > 뷰포트 메타 태그


```html
<meta name="viewport" content="width=device-width, initial-scale=1" />
```
### media query 템플릿
```css
@media screen and (min-width:1024px) {
	/* Desktop */
}
@media screen and (min-width:768px) and (max-width: 1023px) {
	/* Tablet */
}
@media screen and (max-width:767px){ 
	/* Mobile */
}
```
### 분기점 적용 방식 2가지
1. 큰 데스크톱 우선적 제작
2. 가장 작은 디바이스 우선적 제작 / `MDN` 모바일 퍼스트 방식 선호! ⭐
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/4b7f1b94-8734-4662-82bf-284c6f624a1f)

### 😛4단계형 분기점
```
노트북과 태블릿 가로 : 1024px ~ 1279px
태블릿 가로 : 768px ~ 1023px
모바일 가로 & 태블릿 세로 : 480px ~ 767px
모바일 : ~479px

⭐ 또다른 4단계형
// Small devices (landscape phones, 576px and up)
@media (min-width: 576px) { ... }

// Medium devices (tablets, 768px and up)
@media (min-width: 768px) { ... }

// Large devices (desktops, 992px and up)
@media (min-width: 992px) { ... }

// Extra large devices (large desktops, 1200px and up)
@media (min-width: 1200px) { ... }
```
### 😛3단계형 분기점
```
PC : 1024px ~
태블릿 가로, 세로 : 768px ~ 1023px
모바일 가로, 세로 : ~768px
```
### 😛커스텀 분기점
```
@media screen and (max-width: 1680px) {}
@media screen and (max-width: 1400px) {} 
@media screen and (max-width: 1280px) {} 
@media screen and (max-width: 1199px) {}
@media screen and (max-width: 1024px) {} 
@media screen and (max-width: 991px) {} 
@media screen and (max-width: 767px) {} 
@media screen and (max-width: 600px) {}
@media screen and (max-width: 575px) {} 
@media screen and (max-width: 480px) {} 
@media screen and (max-width: 360px) {}
```


---
> [참고자료](https://www.daleseo.com/css-media-queries/)
- `if` 문 같은 역할 ✔
- 😛 주의사항 >> 기본 스타일링 적용하면 안되고 미디어 쿼리에만 넣어야됨!!


```css
@media (조건) {
}
```
### 스타일링
- 핸드폰처럼 좁은 화면 특정 스타일 적용
### `@media` 
> [참고자료](https://uxkm.io/publishing/css/03-cssMiddleclass/09-css_media_part1#gsc.tab=0)
- 미디어별 스타일 지정
- 디바이스뿐 아닌 디바이스 크기&비율 구분 가능
#### 1. 미디어 유형 
|미디어유형|설명|
|:-:|:-:|
|`all`|기본값 / 모든 미디어 장치(print | screen | speech) 사용|
|`print`|프린터 사용|
|`screen`|컴퓨터, 테블릿, 스마트포 등 `스크린` 존재하는 매체 사용|
|`speech`|웹 페이지 읽어주는 화면 낭독기!|

#### 2. 미디어 기능
- 뷰포트 크기에 따라 미디어 쿼리 적용
	- ![image](https://github.com/hyunolike/info-docs/assets/61215550/c6f627e4-4ed8-4746-9ae4-62eb99904f3d)
- `width`
	- 뷰포트의 너비, 높이


```js
<style>
/* 모든 장치에서 최소 너비 20em 이상이면 적용 */
@media (min-width: 20em) { … }

/* 뷰포트 너비가 768px 이상 '그리고' 1024px 이하이면 실행 */
@media all and (min-width:768px) and (max-width:1024px) { … }

/* 뷰포트 너비가 768px 이거나 '또는' 1024px 이면 실행 */
@media all and (width:768px), (width:1024px) { … }

/* 뷰포트 너비가 768px 이상 '그리고' 1024px 이하가 '아니면' 실행 */
@media not all and (min-width:768px) and (max-width:1024px) { … }

/* 뷰포트 너비가 768px 이하 '또는' 뷰포트의 높이가 800px 이하이면 실행 */
@media all and (max-width:768px), (max-height:800px) { … }
</style>
```


- `device-width` `device-heigth`
	- ⭐스크린의 너비, 높이
- `aspect-ratio`
	- 화면 영역의 가로 세로 비율


```css
/* 가로 화면 비가 1:1 이상일 때 적용. 즉, 화면이 직사각이거나 세로일 때만 적용 */
@media screen and (min-aspect-ratio: 1/1) { … }

/* 뷰포트 너비가 5, 높이가 4 비율이면 실행 */
@media all and (aspect-ratio:5/4) { … }

/* 뷰포트 너비가 5/4 비율 이상이면 실행 */
@media all and (min-aspect-ratio:5/4) { … }

/* 뷰포트 너비가 5/4 비율 이하면 실행 */
@media all and (max-aspect-ratio:5/4) { … }
```


- `device-aspect-ratio`
	- 스크린의 너비와 높이 비율
 	- `너비/높이` 순으로 조건 작성
 

```css

/* 장치 가로 세로 비가 16:9일 때 적용 */
@media screen and (device-aspect-ratio: 16/9) { … }

/* 스크린 너비가 5, 높이가 4 비율이면 실행 */
@media all and (device-aspect-ratio:5/4) { … }

/* 스크린 너비가 5/4 비율 이상이면 실행 */
@media all and (min-device-aspect-ratio:5/4) { … }

/* 스크린 너비가 5/4 비율 이하면 실행 */
@media all and (max-device-aspect-ratio:5/4) { … }
```


- 🔥 `orientation`
	- 뷰포트의 너비와 높이 비율을 이용 > 가로모드 인지 세로모드인지 판단!
	- value: `portrait` `landscape`
 	- Applies to: `bitmap media types`
  	- Accepts min/max prefiexs: `no`

#### 3. 미디어 논리 연산자
- `not` `and` `only`
- `,` 쉼표로 구분해서 하나의 규칙 만듬!
##### 3-1. `and` 연산자
- 미디어 결합


```css
/* 뷰포트의 너비가 최소 400픽셀 이상이고 장치가 가로 모드인 경우 */
@media screen and (min-width: 400px) and (orientation: landscape) 
```
##### 3-2. `or` `,(쉼표)` 연산자
- 각각 개별 미디어 쿼리 인식
##### 3-3. `not` 연산자
- 미디어 쿼리 부정
##### 3-4. `only` 연산자
- 전체 쿼리와 일치하는 경우에만 스타일 적용
#### 4. 미디어 쿼리 문법
```js
<style>
/* 뷰포트 너비가 768px 이상 '그리고' 1024px 이하이면 실행 */
@media all and (min-width:768px) and (max-width:1024px) { … }

/* 뷰포트 너비가 768px 이거나 '또는' 1024px 이면 실행 */
@media all and (width:768px), (width:1024px) { … }

/* 뷰포트 너비가 768px 이상 '그리고' 1024px 이하가 '아니면' 실행 */
@media not all and (min-width:768px) and (max-width:1024px) { … }

/* 스크린 너비가 320px '그리고' 높이가 480px 이면 실행 */
@media all and (device-width:320px) and (device-height:480px) { … }

/* 스크린 너비가 최소 320px 이상 '그리고' 높이가 최소 480px 이상이면 실행 */
@media all and (min-device-width:320px) and (min-device-height:480px) { … }
</style>
```
#### 5. css 코드 외부 분기 방법
- ⭐ 이 방법은 `성능 최적화` 측면에서 권장 하지 않음!@!!!!@!@


```html
<!--
데스크탑 브라우저 사용자가 언제든 조건을 변경(예를 들면 창 크기를 조절해서 해상도를 바꿈)할 수 있기 때문에
웹 브라우저는 조건에 관계 없이 A.css 파일과 B.css 파일을 항상 요청합니다.
HTTP 요청을 불필요하게 두 번 발생시켜 이 페이지를 처음 로딩하는 사용자에게는 성능 저하의 원인이 됩니다.
CSS 파일은 하나로 병합하고 CSS 코드 내부에서 조건 분기하는 방식을 권장합니다.
-->
<link rel="stylesheet" type="text/css" media="all and (조건A)" href="A.css">
<link rel="stylesheet" type="text/css" media="all and (조건B)" href="B.css">

<!-- 스크린 장치 최소 화면이 500px보다 크고 800px보다 작을 때 스타일 적용 -->
<link rel="stylesheet" media="screen and (min-width: 500px) and (max-width: 800px)" href="rwd.css">
```

