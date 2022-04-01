## `Spring JPA` - insertable, updatable
- 보통 jpa는 `SAVE` 진행 시, 모든 칼럼을 >> `INSERT` 
- 그럴 경우, NOT NULL로 설정된 칼럼은 >> NULL 삽입 시도
- 쿼리에서 아예 빼버리자!!
- 쿼리에서 제외된 칼럼은 DB에 지정된 `default` 값으로 삽입!! ⭐

### 특정 칼럼을 제외하고 save하는 방법
```java
@Colume(insertable=false, updatable=false)
private String defualtField;
```
