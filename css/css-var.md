## css 변수
> [참고자료](https://www.daleseo.com/css-variables/)
- css variables
### css 변수 정의
```css
.div-name {
  --color: red;
}
```
### css 변수 접근
```css
.ex {
  --gray: #ccc;
  background: var(--gray);
}
```
### css 변수 기본값
```css
.ex {
  color: var(--color, black);
}
```
## ⭐전역 변수
![image](https://github.com/hyunolike/info-docs/assets/61215550/360d2574-3529-48be-8929-48f2c10c2fe5)

