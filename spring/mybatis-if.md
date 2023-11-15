## `Mybatis` 동적쿼리 if문
> [참고자료](https://taesikman1.tistory.com/24)

- 단일 if문
  - if else 문과 다름
 

```xml
😛 파라미터 사용할 경우

<if test='파라미터명 != null'
  and a.product = #{파라미터명}
</if>
```
