## SQL View + JPA entity
> [참고자료](https://joomn11.tistory.com/107)
- view
  - 데이터베이스 가상 테이블
  - 복잡한 sql 간소화 시키기 위함
- ⭐3가지 방법
  - `@Table`
  - `@Subselect`
  - `복합키 view (@IdClass + @Table)`
### `@Table`
1. view 생성 (sql 단)
3. entity 생성 (코드 단)



```java
CREATE OR REPLACE VIEW ROLE AS 
SELECT u.user_id,
       ut.user_id AS u_id
FROM   USER u
       JOIN user_team ut
         ON u.id = ut.user_id;

@Entity
@Immutable
@Table(name = "role")
@Getter
public class Role {

    private String userId;
    
    @Id
    private UUID uId;

    private UUID teamId;

}
```
### `@Subselect`
- sql 뷰 생성하지 않고 어노테이션 코드단에서만 생성 가능


```java
@Entity
@Immutable
@Subselect("SELECT u.user_id,\r\n" + 
        "       ut.user_id AS u_id,\r\n" + 
        "FROM   USER u\r\n" + 
        "       JOIN user_team ut\r\n" + 
        "         ON u.id = ut.user_id")
@Getter
public class Role {

    private String userId;
    
    @Id
    private UUID uId;

    private UUID teamId;

}
```

### 복합키 뷰 (`@IdClass + @Table`)
```java
CREATE OR REPLACE VIEW ROLE AS 
SELECT u.user_id,
       ut.user_id AS u_id,
       tpr.team_id,
       tpr.page_id
FROM   USER u
       JOIN user_team ut
         ON u.id = ut.user_id
       JOIN uteam t
         ON t.id = ut.team_id
       JOIN team_page_role tpr
         ON t.id = tpr.team_id;


@Entity
@Immutable
@Table(name = "role")
@Getter
@IdClass(RoleId.class)
public class Role {

    private String userId;
    private UUID uId;

    @Id
    private UUID teamId;

    @Id
    private UUID pageId;

}

@NoArgsConstructor
@EqualsAndHashCode(onlyExplicitlyIncluded = true)
public class RoleId implements Serializable {

    private static final long serialVersionUID = 1122593031541339037L;

    @EqualsAndHashCode.Include
    UUID teamId;

    @EqualsAndHashCode.Include
    UUID pageId;
}
```
