## 해당 클래스의 요소를 일괄 동작시키기
> [참고자료](https://we-always-fight-with-code.tistory.com/19)
### 자주 사용하는 패턴이야
```js
1. 임시 변수에 문서속 액션을 주고자 하는 클래스명 대입
2. 반복문으로 해당 클래스 부품의 개수만큼 돌리기
3. 임시 변수를 배열로 사용해 임시배열변수에 액션 지정

function myFunction() { 
  var x = document.getElementsByClassName("class-name"); 
  for (var i = 0; i < x.length; i++) { 
    x[i].style.display = "none"; 
  } 
}​
```
### 기본 상식이야 
- 아이디 >  여러 요소 지정 불가 + 단 하나의 요소만 가능
- 클래스 > 같은 이름으로 여러 요소 지정 가능
