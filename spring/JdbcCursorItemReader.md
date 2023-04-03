## Spring batch - JdbcCursorItemReader
> [참고자료](https://ojt90902.tistory.com/783)

### JdbcCursorItemReader
- Cursor 기반의 JDBC 구현체 
  - Cursor 가리키는 지점에서 한번에 `Fetch Size 만큼 DB에서 메모리로 올린다는 이야기`  
  - 💡 `Fetch Size == Chunk Size` 맞춰주는 것이 좋음
- ResultSet 함께 사용
