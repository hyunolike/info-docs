## 반복문 한번에 빠져나오기
> [참고자료](https://ko.javascript.info/while-for#ref-347)
- 여러개의 중첩문 한 번에 빠져나오는 경우 사용!


```js
⭐ outer > labelName

outer: for (...) {
  for (...) {
    if(조건) break outer 
  }
}
```
### 주의
- 반드시 레이블은 `break` `continue` 지시자 위에 사용!
