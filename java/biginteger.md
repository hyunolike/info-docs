## 자바에서 큰 숫자(정수) 다루기 >> `BigInteger`
### 왜 사용? 

|Type|범위|
|------|-------|
|`int`|-2,147,483,648 ~ 2,147,483,647|
|`long`|-9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807|
- `int`: 4바이트 표현 가능 범위
- `long`: 8바이트 표현 가능 범위
- ✔ 위 범위를 넘게 되면 `0` 으로 출력 ㅠ,ㅠ
  - 보통은 넘을 경우가 없지만, 금융, 돈과 관련된 개발 및 알고리즘 문제 시 무한의 정수가 들어갈 가능성이 있다면 `BigInteger` 클래스 활용!

### `BigInteger` 사용법
#### 선언
```java
BigInteger bigNum = new BigInteger("10000");
```
- `java.math` 패키지
- 초기화하기 위해서 인자 값( __문자열__ ) 넘겨주자
  - 왜냐면!! BigInteger은 문자열로 되있으니까
#### 계산
- 해당 클래스의 내부 클래스 사용!
```java
BigInteger bigNum1 = new BigInteger("100000");
BigInteger bigNum2 = new BigInteger("10000");

System.out.println("덧셈" + bigNum1.add(bigNum2));
System.out.println("뺄셈" + bigNum1.substract(bigNum2));
System.out.println("곱셈" + bigNum1.multiply(bigNum2));
System.out.println("나눗셈" + bigNum1.divide(bigNum2));
System.out.println("나머지" + bigNum1.remainder(bigNum2));
```

#### 두 수 비교
```java
BigInteger bigNum1 = new BigInteger("10000"); 
BigInteger bigNum2 = new BigInteger("10000000");

int compare = bigNum1.compareTo(bigNum2);
System.out.println(compare);
```

