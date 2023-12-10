## null check, 빈 값 체크
> [참고자료](https://sanghaklee.tistory.com/m/3)


```js
var value = ""
if(!value) { ⭐️
  console.log("비어 있음");
}else {
  console.log("값이 있음");
}
```


- `false` 반환 값 >> `""`, `null`, `undefined`, `0`, `NaN`
- `true` 반환 값 >> 나머지 모두!!
