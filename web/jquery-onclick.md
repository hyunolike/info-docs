## `jquery` onclick 이벤트 중복 해결
> [참고자료](https://tmdrnr96.tistory.com/19)
- 클릭 시 1회 실행해야 되지만 종종 여러번 실행되는 경우 발생
- 요소 감싸고 있는 부모태들도 클릭 이벤트에 반응하기 때문 >> 버블링 현상🔥

### 이벤트 버블링 해결 방법
#### 1. ` off `이용
```js
//모든 이벤트 제거하기
#("#id").off().on("click",funtion(e){
	//do someting
});

//특정 이벤트만 제거하기(click 이벤트만 제거)
$("#id").off("click").on("click",funtion(e){
	//do something
});
```

#### 2. `.unbind()` `bind()` 이용
```js
//unbind 후 bind 하기
$("#id").unbind("click").bind("click",funtion(e){
	//do something
});
```

#### 3. `stopPropagation()`
```js
//부모 태그로의 이벤트 전파를 멈춘다.
$("#id").on("click",funtion(e){
	e.stopPropagtion();
    //do Something
});
```

#### 4. `.preventDefault()`
- 해당 이벤트 외에 별도의 브라우저 행위를 막기 위한 방법


```js
$("#id").on("click",funtion(e){
	e.preventDefault();
    //do Something
});

```
