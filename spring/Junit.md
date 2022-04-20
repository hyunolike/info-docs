## `JUnit` 
> 자바와 JUnit 활용한 실용주의 단위 테스트

```java
01     package iloveyouboss;
02

03    import static org.junit.Assert.;
04    import static org.hamcrest.CoreMatchers.;
05    import org.junit.*;
06

07    public class ScoreCollectionTest {
08        @Test
09        public void answersArithmeticMeanOfTwoNumbers() {
10            // 준비⭐
11            ScoreCollection collection = new ScoreCollection();
12            collection.add(() -> 5);
13            collection.add(() -> 7);
14

15            // 실행⭐
16            int actualResult = collection.arithmeticMean();
17

18            // 단언⭐ ✌다양한 JUnit 단언을 배우자!!!
19            assertThat(actualResult, equalTo(6));
20        }
21    }
```

### 어떤 테스트 작성할 수 있는지 결정
- 분기점
- 잠재적으로 영향력 큰 데이터 변형들 

### `@Before` 메서드로 테스트 초기화
- 모든 테스트 코드에 포함되어 있는 __공통적인 초기화 코드__

### `JUnit` 단언 배우기
- 테스트에 넣을 수 있는 정적 메서드 호출
#### `assertTrue`
- 단언은 Junit 테스트에서 광범위하게 사용되기 떄문에 대부분의 프로그래머는 군더더기를 줄이고자 __정적 임포트__ 사용
- `import static org.junit.Assert.*;`

#### `assertThat` 
- 대부분 단언 >> 기대하는 값과 반환된 실제 값을 비교
- `assertThat(account.getBalance(), equalTo(100));`

#### `is` 장식자
- 매처 표현의 가독성 높여줌
- 단지 넘겨받은 매처를 반환할 뿐(즉, 아무것도 안함)

#### 단언 설명
- `assertThat()`

### 예외처리 3가지
#### `@Test`
- `@Test(expected=InsufficientFundsException.class)`

#### `try/catch와 fail` 옛날 방식!
```java
try {
    account.withdraw(100);
    fail();
}
catch (InsufficientFundsException expected) {
}
```
### `ExpectedException` 새로운 방식
```java
01     import org.junit.rules.*; 
02    // ... 
03        @Rule 
04        public ExpectedException thrown = ExpectedException.none();
```

