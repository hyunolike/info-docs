## `MariaDB` 뷰 테이블 생성
- 뷰는 일반 사용자 입장에서 ✔ 테이블과 동일하게 사용되는 객체 
- `SELECT` 문으로 만들어진 테이블 >> 뷰 테이블
- 기본적으로 읽기 전용!
- 보안에 도움 / __특정 정보__ 만 조회할 수 있도록 제공!
---
- 쿼리문으로 생성하는 가상적인 테이블

### 1. 뷰 생성
```SQL
USE 스키마명

CREATE VIEW 뷰 테이블명
  AS SELECT 
    a.col1 as '칼럼1',
    a.col2 as '칼럼2',
    a.col3 as '칼럼3'
    FROM 테이블1 a INNER JOIN 테이블2 b on a.Id = b.Id
```

### 2. 뷰 수정
```sql
ALTER VIEW 뷰 테이블명 
   AS SELECT 
    a.col1 as '칼럼1',
    a.col2 as '칼럼2',
    a.col3 as '칼럼3' 
    FROM 테이블1 a INNER JOIN 테이블2 b on a.Id = b.Id
```

### 3. 뷰 삭제
```SQL
DROP VIEW 뷰 테이블명
```

### 4. 뷰 정보 확인
```SQL
DESCRIBE VIEW 뷰 테이블명
```

### 5. 뷰 소스코드 확인
```SQL
SHOW CREATE VIEW 뷰 테이블명
```

## 뷰의 종류
### 수평, 수직 뷰
- 수직 뷰
  - 테이블의 일부 필드만 가지는 뷰
  - ![image](https://user-images.githubusercontent.com/61215550/162373981-1a3015f3-f01e-4fa2-8984-a94cd32e4851.png)

- 수평 뷰
  - 테이블의 일부 레코드만으로 구성한 뷰 
  - ![image](https://user-images.githubusercontent.com/61215550/162374000-0b17a9eb-7133-406a-8f47-9774cc19fe9b.png)
- 수평, 수직 둘다 적용 가능하다!!

### 필드 이름 변경
```sql
CREATE VIEW vView(n, d, s) AS
  SELECT name, depart, salary FROM tStaff
```
- ![image](https://user-images.githubusercontent.com/61215550/162374221-0109818f-cb2b-4df8-84cf-9eeb4f55a4ea.png)
