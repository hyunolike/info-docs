## 숫자 천단위 찍기
> [참고자료](https://coding-factory.tistory.com/734)
### `DecimalFormat`
```java
int amount = 1000000000;
DecimalFormat df = new DecimalFormat("###,###");
String money = df.format(amount);
System.out.println(money);
```

### 정규식
```java
String amount = "1000000000";
amount = amount.replaceAll("\\B(?=(\\d{3})+(?!\\d))", ",");
System.out.println(amount);
```
