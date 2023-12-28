## `querydsl` DATE_FORMAT
> [참고자료](https://jjunn93.com/entry/QueryDSL-DATEFORMAT-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0)
- ⭐사용 가능 함수
  - `Expressions.StringTemplate()` `Expressions.numberTemplate()`
### `DATE_FORMAT` 구분기호
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/19df1282-a517-4457-83a5-f38ea505b36a)
### QueryDSL 사용
#### 1. `Expressions.StringTemplate(MySQL 문법, {0} 변경할 값, {1s} 변경할 양식)`
```java
StringTemplate dateFormat = Expressions.stringTemplate(
  "DATE_FORMAT({0}, '{1s}')", '2023-12-28', ConstantImpl.create("%Y-%m-%d")
)
```
#### 2. `Expressions.dateTemplate(표현 유형, MySQL 문법, {0} 변경할 값, {1s} 변경할 양식)`
```java
StringTemplate dateFormat = Expressions.dateTemplate(
  String.class, "DATE_FORMAT({0}, '{1s}')", "2023-12-28", ConstantImpl.create("%Y-%m-%d")
) 
```
