## `union` 전체 정렬
> [참고자료](https://mainia.tistory.com/70)


```sql
-- 다음과 같이 적용시켯다
SELECT TOP * FROM (
select * from (SELECT TOP 5 No, Title, Idate, path = '/Border/CellPhoto' FROM tbCellPhoto ORDER BY No DESC) AS a1
UNION ALL
select * from (SELECT TOP 5 No, Title, Idate, path = '/Border/Confession' FROM tbConfession ORDER BY No DESC) AS a2
) AS a3
ORDER BY Idate DESC
```
