## `querydsl` 상수 넣기
> [참고자료](https://ttl-blog.tistory.com/222)
```java
/**
 * 상수
 * Expressions 사용
 */
@Test
fun testConstant() {
    //given
    val fetch = query
        .select(member.username, Expressions.constant("A"))
        .from(member)
        .fetch()

    fetch.forEach { println(it) }
}
출처: https://ttl-blog.tistory.com/222 [Shin._.Mallang:티스토리]
```
