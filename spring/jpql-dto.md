## `JPQL` DTO 사용
> [참고자료](https://velog.io/@youmakemesmile/Spring-Data-JPA-JPQL-%EC%82%AC%EC%9A%A9-%EB%B0%A9%EB%B2%95Query-nativeQuery-DTO-Mapping-function)

### DTO Mapping
```java
public interface UserRepository extends JpaRepository<User, String> {
    @Query(value = "select " +
            "new io.velog.youmakemesmile.jpql.UserDto(user.id, user.name, user.phone, user.deptId, dept.name) " +
            "from User user " +
            "left outer join Dept dept on user.deptId = dept.id ")
    List<UserDto> findUserDept();
}
```

