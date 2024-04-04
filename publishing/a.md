## 통 이미지에 있는 버튼 동작하게 만들기 `<a>` 태그 활용
- <img width="562" alt="image" src="https://github.com/hyunolike/info-docs/assets/61215550/8bdd988c-5bcc-4a46-a1f1-659fdbf611d1">
### 코드
```
<div>
  <a href="#">오픈 알림 신청 하기</a>
</div>

...
div {
  display: relative; ⭐️
}

a {
  overflow: hidden;
  text-decoration: none;
  font-size: 0;

  display: absolute; ⭐️
  top: ...
  left: ...
}

```
