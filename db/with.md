## WITH (임시테이블)
> [참고자료](https://inpa.tistory.com/entry/MYSQL-%F0%9F%93%9A-WITH-%EC%9E%84%EC%8B%9C-%ED%85%8C%EC%9D%B4%EB%B8%94)
```sql
WITH TEMP_TABLE as 
(
    SELECT NAME, count(NAME) 
    FROM ANIMAL_INS
    WHERE NAME IS NOT NULL
    GROUP BY NAME
    ORDER BY NAME
)

SELECT * FROM TEMP_TABLE
WHERE COUNT > 1
출처: https://inpa.tistory.com/entry/MYSQL-📚-WITH-임시-테이블 [Inpa Dev 👨‍💻:티스토리]
```


- 🔥 동일한 sql 반복 사용 > 성능 높이기위해 사용
- `with` 가상테이블 > 메모리 차지
### 예시
```sql
[기존]
select job, sum(sal)
from emp
group by job
having sum(sal) > (select avg(sum(sal)) from emp group by job) ;

[임시 테이블]
with eee as
(
	select job, sum(sal) as total 
    from emp 
    group by job
)

select job, total 
from eee
where total > (select avg(total) from eee);
```
