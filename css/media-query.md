## media query `updated by 2023/09/21`
### 단계별 반응형 개발 예시
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


