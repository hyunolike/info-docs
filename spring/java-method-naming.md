## 좋은 코드를 위한 자바 메서드 네이밍
> [참고자료](https://tecoble.techcourse.co.kr/post/2020-04-26-Method-Naming/)
- ⭐ 네이밍 중요 이유
  - 코드 가독성


```java
// 이름이 명확히 변경
public List<int[]> getFlaggedCells() {
    List<int[]> flaggedCells = new ArrayList<int[]>();
    for (int[] cell : gameBoard) {
        if (cell.isFlagged()) {
        	flaggedCells.add(cell);
        }
    }
    return flaggedCells;
}
```
### 네이밍시 중요한 고려사항
- 왜 존재?
- 무슨 작업?
- 어떻게 사용?


```java
public List<Piece> findPiecesByColor(Color color){}
// 왜 존재해야 하는가 - color에 대해 존재하는 piece들을 알기 위해.
// 무슨 작업을 하는가 - color에 맞는 piece들을 가져온다.
// 어떻게 사용하는가 - 체스판에서 흑색(or 백색)의 piece들을 가져와서 점수를 계산.
```


### 메서드 명명 규칙
- 메서드 이름 `lowerCamelCaes`
- 메서드 이름 **동사/전치사** 사용


```java
// Example
// 동사
public void getUserByName(){}
public void setDisplayName(){}
public void inputData(String input){}
    
// 전치사
public String toString(){}
public User of(){}
```
#### 💡 Junit 테스트 메소드 - `_` 표시되어 이름의 논리 컴포넌트를 구분
```java
// Example
// 1. MethodName_StateUnderTest_ExpectedBehavior (메서드명_테스트상태_기대행위)
@Test
void isAdult_AgeLessThan18_False(){}

// 2. MethodName_ExpectedBehavior_StateUnderTest (메서드명_기대행위_테스트상태)
@Test
void isAdult_False_AgeLessThan18(){}
```

### 메서드 이름으로 자주 사용되는 동사
|동사|설명|
|--|--|
|`get/set`|...|
|`init`|데이터를 초기화하는 메서드명|
|`is/has/can`|- boolean 값 리턴<br>- `is` 맞는지 틀린지 판단하는 메서드 명<br>- `has` 데이터 가지고 있는지 확인<br>- 할 수 있는지 없는지 확인|
|`create`|새로운 객체 만든 후 리턴해주는 메서드 명|
|`find`|데이터 찾는 메서드명|
|`to`|해당 객체를 다른 형태의 객체로 변환해주는 메서드 명|
|`A-By-B`|B를 기준으로 A를 하겠다는 의미<br> `getUserByName`  Ex) Name을 기준으로 User를 get하는 메서드 |
