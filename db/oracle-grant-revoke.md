## 오라클 시스템 권한 부여 방법
> [참고자료](https://gent.tistory.com/534)
- ![image](https://user-images.githubusercontent.com/61215550/224530394-474ca61e-9da2-4a3c-ac16-9eb5f2182365.png)

### 1. 데이터베이스 접속 권한 `CREATE SESSION`
```sql
GRANT CREATE SESSION TO scott
```


- 사용자 생성 후 세션 권한 부여되어야 데이터베이스 접속 가능
- 세션 부여하지 않으면 >> `ORA-01045: 사용자 SCOTT는 CREATE SESSION 권한을 가지고있지 않음; 로그온이 거절되었습니다`

### 2. 테이블 생성 권한 
```SQL
GRANT CRETAE TABLE TO scott
```


- 테이블 생성 권한 부여되면 자신의 스키마에 테이블 생성 및 삭제 가능
- `CREAT ANY TABLE` 권한 부여 시 다른 사용자의 스키마에 테이블 생성 가능


### 3. 테이블스페이스 사용 권한
```sql
GRANT UNLIMITED TABLESPACE TO scott
```


- 일반 사용자가 모든 테이블스페이스 제한 없이 사용하는 것은 운영 측면에서 좋지 않음(아래처럼 적용하기)


```sql
ALTER USER scott QUOTA 10M ON tblspace1
-- alter [사용자명] quota [제한용량] on [테이블스페이스명]
```

### 4. 인덱스 생성 권한
```sql
GRANT CREATE ANY INDEX TO scott;
GRANT DROP ANY INDEX TO scott;
```
### 요약
<img width="791" alt="image" src="https://user-images.githubusercontent.com/61215550/224530577-1146f8cd-3f8a-459b-ae01-5ef8d024199f.png">

