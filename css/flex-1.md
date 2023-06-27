## `flex:1`
> [참고자료](https://velog.io/@mooongs/flex1%EC%9D%98-%EC%9D%98%EB%AF%B8)
- `flex`: `flex-grow` + `flex-shrink` + `flex-basis`
### `flex:1` ??
```css
flex-grow: 1;
flex-shrink: 1;
flex-basis: 0%

⭐ 두개의 div 동일한 크기로 반반 이야!!
.inc-exp-container > div {
    flex: 1;
    text-align: center;
}
```


- 😛`flex-basis` 0 >> 화면 비율에 따라 유연하게 크기 조절 가능
