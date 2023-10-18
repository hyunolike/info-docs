## `MariaDB` 검색값 변수로 만들어서 select하는 방법
> [참고자료](https://nasn.tistory.com/107)
### 1. 검색값 변수로 지정
```sql
set @value = ([SELECT SQL]);

set @value = (select id from object_user where idx=1);
```
### 2. 해당 변수값으로 검색
```sql
select * from object_user where id=@value
```
