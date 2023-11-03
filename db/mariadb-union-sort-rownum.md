## `UNION` 쿼리 이용 후 정렬 + ROWNUM 생성하는 방법!
> [참고자료](https://dorongdogfoot.tistory.com/25)


### 베이스 코드
```sql
SELECT ROWNUM() OVER(ORDER BY 칼럼명 ASC) AS rownum, ... (
  SELECT * FROM TABLE1 LEFT JOIN TABLE1-1 ON TABLE1.A = TABLE1-1.B
  UNION
  SELEC * FROM TABLE2 LEFT JOIN TABLE2-1 ON TABLE2.A = TABLE2-1.B
) AS TMP ORDER BY rownum DESC;

# 해석
- TABLE1, TABLE2 합집합
- TMP 라는 임시 테이블에 묶어서 ROWNUM 생성! 이거는 칼럼에 ASC 정렬된 기준으로 만들고
- 다시 거꾸로 DESCS 정렬해
- 그러면 가장 최근 수정된 칼럼(이거) 기준으로 거꾸로 rownum 출력되게 만들 수 있다!
```


![image](https://github.com/hyunolike/info-docs/assets/61215550/02e031a7-dd9e-4da6-8039-ba258ac632fa)
