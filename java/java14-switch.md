## 자바14 개선된 `switch`
> [참고자료](https://hseungyeon.tistory.com/453)


```java
switch (day) {
    case MONDAY, FRIDAY, SUNDAY	-> System.out.println(6);
    case TUESDAY -> System.out.println(7);
    case THURSDAY, SATURDAY -> System.out.println(8);
    case WEDNESDAY -> System.out.println(9);
}
```
### 특징
- 다중 case 사용
- 화살표 사용하면 마지막에 `break` 사용한 것과 동일
- 실행문 2줄 이상일 때는 중괄호 필수
