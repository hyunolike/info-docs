## `scss` (Synthentically Awesome StyleSheets)
> [참고자료](https://seokzin.tistory.com/entry/SCSS-SCSS-%EB%AC%B8%EB%B2%95-%EC%A0%95%EB%A6%AC)
- `Sass` 로 부턷 등장
  - sass: css 전처리기 > 변수, 상속, 혼합, 중첩 등 다양한 기능 제공
### 개념
- `Sass` 3버전부터 새롭게 등장
  - scss > Sass의 모든 기능 지원 `Superset`
- 주요 차이
  - Sass: 중괄호 아닌 `들여쓰기` 사용
  - SCSS: CSS처럼 `{}` + `;` 사용

### 문법
#### 1. 데이터 타입
- 변수처러 사용 가능
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/43bdd4b8-05d4-4bc6-8d48-77eb5f33f512)
#### 2. 중첩
- 상위 선택자의 반복 


```scss
.section {
  width: 100%;
  
  .list {
    padding: 20px;
    
    li {
      float: left;
    }
  }
}

```
##### 3. `&` 싱위 선택자 참조
```scss
/* SCSS */

.btn {
  position: absolute;
  
  &.active {
    color: red;
  }
}

.list {
  li {
    &:last-child {
      margin-right: 0;
    }
  }
}

/* SCSS */

.btn {
  position: absolute;
  
  &.active {
    color: red;
  }
}

.list {
  li {
    &:last-child {
      margin-right: 0;
    }
  }
}

```
##### 4. 변수
```css
$color-primary: #e96900;
$url-images: "/assets/images/";
$w: 200px;

.box {
  width: $w;
  margin-left: $w;
  background: $color-primary url($url-images + "bg.jpg");
}

```
#### 5. Variable Scope
```scss
.box1 {
  $color: #111;
  background: $color;
}
```
#### 6. #{} 어디서든 변수 넣기!~~~
```scss
 /* SCSS */
$family: unquote("Droid+Sans");
@import url("http://fonts.googleapis.com/css?family=#{$family}");
```
#### 7. 연산
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/badcfe44-a5b1-411e-aed2-25943ba2d332)

#### 8. Mixins (재활용)
```scss
/* 선언 - @mixin */

@mixin large-text {
  font: {
    size: 22px;
    weight: bold;
    family: sans-serif;
  }
  color: orange;

  &::after {
    content: "!!";
  }

  span.icon {
    background: url("/images/icon.png");
  }
}


/* 사용 - @include */

h1 {
  @include large-text;
}

div {
  @include large-text;
}
```
#### 9. Functions
- `Minin`: 지정한 스타일 반환
- `함수`: 계산된 특정 값을 @return 지시어 통해 반환


```scss
$max-width: 980px;

@function columns($number: 1, $columns: 12) {
  @return $max-width * ($number / $columns);
}

.box_group {
  width: $max-width;

  .box1 {
    width: columns(); // 1
  }
  
  .box2 {
    width: columns(8);
  }
  
  .box3 {
    width: columns(3);
  }
}
```
#### 10. 조건
##### 10-1. if
```scss
/* SCSS */
$width: 555px;

div {
  width: if($width > 300px, $width, null);
}
```
##### 10-2. @if @else @else if
```scss
/* SCSS */

$color: orange;

div {
  @if $color == strawberry {
    color: #fe2e2e;
  } @else if $color == orange {
    color: #fe9a2e;
  } @else if $color == banana {
    color: #ffff00;
  } @else {
    color: #2a1b0a;
  }
}
```
#### 11. 반복
##### 11-1. @for
```scss
/* SCSS */

/* 1부터 3까지 반복 (3번 반복) */

@for $i from 1 through 3 {
  .through:nth-child(#{$i}) {
    width: 20px * $i;
  }
}


/* 1부터 3 직전까지 반복 (2번 반복) */

@for $i from 1 to 3 {
  .to:nth-child(#{$i}) {
    width: 20px * $i;
  }
}


/* Compile to CSS */

.through:nth-child(1) {
  width: 20px;
}

.through:nth-child(2) {
  width: 40px;
}

.through:nth-child(3) {
  width: 60px;
}

.to:nth-child(1) {
  width: 20px;
}

.to:nth-child(2) {
  width: 40px;
}
```
##### 11-2. @each
```scss
/* SCSS */

// List
@each $animal in puma, sea-slug, egret, salamander {

  .#{$animal}-icon {
    background-image: url('/images/#{$animal}.png');
  }
}

// Map
@each $header, $size in (h1: 2em, h2: 1.5em, h3: 1.2em) {
  #{$header} {
    font-size: $size;
  }
}


/* Compile to CSS */

.puma-icon {
  background-image: url("/images/puma.png");
}

.sea-slug-icon {
  background-image: url("/images/sea-slug.png");
}

.egret-icon {
  background-image: url("/images/egret.png");
}

.salamander-icon {
  background-image: url("/images/salamander.png");
}

h1 {
  font-size: 2em;
}

h2 {
  font-size: 1.5em;
}

h3 {
  font-size: 1.2em;
}
```
#### 12. 내장함수
- 기본 내장함수 제공


```scss
.item:nth-child(1) {
  background-color: $color;
}
.item:nth-child(2) {
  background-color: lighten($color, 20%);
}
.item:nth-child(3) {
  color: white;
  background-color: darken($color, 20%);
}
.item:nth-child(4) {
  background-color: grayscale($color);
}
.item:nth-child(5) {
  background-color: rgba($color, 0.3);
}
.item:nth-child(6) {
  background-color: invert($color);
}
```
