## 2개 이상의 다중칼럼 `PK`
> [참고자료](https://hoon93.tistory.com/57)
- ✔PK: 테이블은 오직 하나의 기본키(PK)를 가질 수 있다 >> 오직 하나의 칼럼이 아님 !!! ⭐
- ✔핵심 >> 칼럼은 2개 이상 가능 / 기본키 복수는 불가능


```sql
ID1 CHAR(4) PRIMARY KEY, 
ID2 CHAR(4) PRIMARY KEY  ❌

CONSTRANINT TABLE 명 PRIMARY KEY(ID1, ID2) ⭕
```
