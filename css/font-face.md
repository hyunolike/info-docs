## @font-face
> [참고자료](https://webclub.tistory.com/m/261)
- 컴포넌트 각 요소 서로 다른 서체 저장!
- 사이트를 볼 때 다운되는 서체 > `웹 폰트`
- `@font-face`: 지시어 사용해 웹 브라우저엑 해당 서체를 다운로드 알림 및 사용

### 웹 폰트 사용
- 2개의 명령어 > `@font-face` `font-family`
  - `@font-face`: 웹 브라우저에게 서체 이름 / 다운받을 위치 알려줌
  - `font-family`: 이걸 통해 사용


```css
@font-face {
    font-family: <a-remote-font-name> ⭐️ 이걸 가져다 사용하면 돼!!
    src: <source> [, <source>]*;
    [font-weight: <weight>];
    [font-style: <style>];
}
```

### 👨‍🌾 Next.js 사용 에시
<img width="647" alt="image" src="https://github.com/hyunolike/info-docs/assets/61215550/d614c284-790d-4688-8b10-324eb8fdda26">
