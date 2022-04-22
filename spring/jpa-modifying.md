## `@Modifying` 
> [참고 자료](https://devhyogeon.tistory.com/4)

```java
@Transactional
@Modifying
@Query(value = "UPDATE SHIPPING_STATUS " +
        "SET BATCH_ID = :BATCHID " +
        "FROM USIMPAY u " +
        "WHERE SHIPPING_STATUS.usimDiv = u.usimDiv ",
        nativeQuery = true)
void updateBatchId(@Param("BATCHID") String batchId);
```

### `@Query`
- 기본적으로 __JPQL__
- `nativeQuery = true` 옵션으로 __네이티브 쿼리__ 가능

### `@Modifying`
- `@Query` 로 작성된 __변경, 삭제__ 쿼리 메서드를 사용할 때 필요
- 조회 쿼리 제외하고 데이터 변경 일어나는 `INSERT` `UPDATE` `DELETE` `DDL` 에서 사용! >> 벌크 연산?

### 벌크 연산
- 다건의 UPDATE, DELETE 연산을 하나의 쿼리로 하는 것
