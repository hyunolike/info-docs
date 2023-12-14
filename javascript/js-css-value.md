## javascript로 `css 변수` 제어
> [참고자료](https://codingeverybody.kr/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%A1%9C-css-%EB%B3%80%EC%88%98-%EC%A0%9C%EC%96%B4%ED%95%98%EA%B8%B0-%EC%A0%91%EA%B7%BC%EA%B3%BC-%EC%84%A4%EC%A0%95-%EB%B0%A9%EB%B2%95/)
### 방법 3가지
#### 1. `window.getComputedStyle()`
- 함수 사용 > css 변수의 현재값 가져오기
#### 2. `document.querySelector()`
- css 변수를 설정할 요소 선택
#### 3. `element.style.setProperty()`
- css 변수 값 설정



```
:root {
    --main-color: blue;
    --font-size: 16px;
}
.target-element {
    color: var(--main-color);
    font-size: var(--font-size);
}


// 1. CSS 변수의 현재 값을 가져오기 위해 window.getComputedStyle() 함수를 사용합니다.
const rootStyles = window.getComputedStyle(document.documentElement);
const targetElement = document.querySelector('.target-element');

const mainColorValue = rootStyles.getPropertyValue('--main-color');
const fontSizeValue = rootStyles.getPropertyValue('--font-size');

console.log(mainColorValue); // 출력 결과: "blue"
console.log(fontSizeValue); // 출력 결과: "16px"

// 2. "Change Styles" 버튼 클릭 시 CSS 변수 값을 변경하여 스타일을 동적으로 조작합니다.
document.getElementById('changeStylesBtn').addEventListener('click', () => {
    // 3. CSS 변수 값을 변경하기 위해 element.style.setProperty() 함수를 사용합니다.
    targetElement.style.setProperty('--main-color', 'red');
    targetElement.style.setProperty('--font-size', '20px');
});
```
