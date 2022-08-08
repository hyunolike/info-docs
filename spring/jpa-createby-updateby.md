## `JPA Auditing` - `@CreateBy` `@UpdateBy` + 📌AuditorAware
> [참고자료](https://velog.io/@ewan/JPA-CreateBy-UpdateBy)
- ⭐ JPA >> DB에서 **데이터 작성인** / **작성일** 에 대한 어노테이션 제공
- 누군지에 대한 어노테이션 제공

```java
@Getter
@MappedSuperclass
public abstract class BaseEntity {

    @CreatedBy
    @Column(name = "create_by", nullable = false)
    private String createBy;

    @LastModifiedBy
    @Column(name = "update_by", nullable = false)
    private String updateBy;

    @CreatedDate
    @Column(name = "create_date", nullable = false)
    private Instant createDate;

    @LastModifiedDate
    @Column(name = "update_date")
    private Instant updateDate;


    @PrePersist
    public void prePersist() {
        this.createBy = SecurityUtils.getByCurrentLoginName().orElse("system");
        this.updateBy = SecurityUtils.getByCurrentLoginName().orElse("system");
    }

    @PreUpdate
    public void preUpdate() {
        this.updateBy = SecurityUtils.getByCurrentLoginName().orElse("system");
    }

}
```
