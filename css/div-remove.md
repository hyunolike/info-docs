## `div` 공백 제거하는 방법
> [참고자료](https://velog.io/@sukjune96/CSS-div%EC%97%90%EC%84%9C-%EA%B3%B5%EB%B0%B1%EC%9D%B4-%EC%83%9D%EA%B8%B0%EB%8A%94-%EA%B2%BD%EC%9A%B0)
### 공백 생기는 이유
```html
<article>
	</img>
    <div></div>
</article>
```


- ![image](https://github.com/hyunolike/info-docs/assets/61215550/d26ead79-b13e-4cd2-9bd9-ac49a9de6fc3)
- 태그 입력 후 엔터 치고 `div` 입력하면 > `html` 에서 엔터를 읽어버려서 발생해
### 해결 방법은?
#### 1. `font-size: 0`
- 두 태그를 가지고 있는 부모 > 개행문자의 폰트 크기가 0 이면 여백 사라짐
- 하지만, 부모태그가 가진 자식 태그들의 폰트 크기가 0 이 되므로 자식 태그에서 다시 폰트 크기 설정 ㅠ,ㅠ
#### 2. `display: block`
- `inline` 속성 가진 img 태그에 > `display: block` 해주면 자식 태그 모두 block 되므로 여백 사라짐!
#### 3. `display: flex`
- 마지막 부모태그 > 위 속성 설정
- 세로 배열하는 경우 > `flex-direction: cloumn` 같이 설정해줘야 돼!
