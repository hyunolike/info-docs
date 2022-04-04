## Oracle `Segment`
- 1개 이상의 `Extent` 모여서 만들어진 거 
- `Object` 중에서 저장 공간 갖는것
- 데이터 담고 있는 테이블 그러나!! 안의 내용에 따라 이름이 달라짐

![image](https://user-images.githubusercontent.com/61215550/161455000-2b27140b-0621-499a-815d-34f00707e03e.png)

### `Object` `Segment` 차이
- `Object`: 오라클에서 데이터 관리하기 위해 생성하는 모든 것 / table, index, view, sequence, synonym 등
- `Segment`: Object 중에서 저장공간 갖고 있는 것들 / index, table / Object가 Segement 포함하는 개념
