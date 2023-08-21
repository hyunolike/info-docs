## css 다중 선택자
> [참고자료](https://ppoote.tistory.com/127)
```css
1.공백없이 클래스끼리 붙어있는 경우
.class1.class2{}  ex)-.name1.name2
클래스 속성 내에 name1과 name2가 모두 설정된 모든 요소를 ​​선택합니다.

2.쉼표가 있는 경우입니다.
element, element, element { style properties }

css 선택자 목록(,)은 일치하는 모든 요소를 선택합니다.

쉼표로 구분한 목록을 한 줄에 배치할 수 있습니다.
h1, h2, h3, h4, h5, h6 { font-family: helvetica; }
 
3. 공백으로 연결해서 사용 하면 하위 개체로 지정합니다.
.a .b .c

a클래스 내부의 b클래스 내부 c클래스요소에만 스타일 적용합니다.

특정 요소의 앞, 뒤 혹은 내부에 있는 것을 선택하는 법  A > B

부모가 A이고 아래 단계인 b요소들만 선택하는 합니다.
class에서 띄어쓰기의 의미 

<div class="park one">park 1</p>

두 클래스를 다 가지게 되는 것 왜냐면 class 이름에 공백은 허용되지 않습니다.
```
