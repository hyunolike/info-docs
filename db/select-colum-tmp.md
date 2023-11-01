## select문에다 존재하지 않는 칼럼 추가하는 방법
> [참고자료](https://www.phpschool.com/gnuboard4/bbs/board.php?bo_table=qna_db&wr_id=174322)



```sql
SELECT "임의값" as temp2, temp1 FROM temp_table WHERE temp1 >=1;
```
