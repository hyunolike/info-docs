## 오라클 문법
### 1. 테이블 생성 `CREATE`

```sql
CREATE TABLE [스키마.]테이블 명(
  칼럼1 칼럼1의 데이터타입 [NULL, NOT NULL],
  ...
  칼럼N 칼럼N의 데이터타입 [NULL, NOT NULL]
);
```

#### 1-1. 제약 조건 `CONSTRAINTS`
- 제약 조건: `NOT NULL` `UNIQUE` `기본키` `외래키` `CHECK` 등 있다!

```sql
CREATE TABLE 테이블 명(
  ...
  CONSTRAINTS set1_unique UNIQUE (칼럼 명)
)

CREATE TABLE 테이블 명(
  ...
  CONSTRAINTS set1_pk PRIMARY KEY(칼럼1, 칼럼2) ✔ PK 1개의 테이블에 다중으로 설정 가능 
)

-- 외래키(반드 참조테이블 먼저생성, 참조키가 참조테이블의 기본키로) 
-- CONSTRAINT 외래키명 FOREIGN KEY(컬럼명, ...) 
-- REFERENCES 참조테이블(참조테이블 컬럼명, ...

-- CHECK(특정조건에 맞는 데이터만 입력받고, 아니면 오류를 뱉음)
CREATE TABLE 테이블 명(
  NM_SEQ NUMBER,
  CONSTRAINTS check1 CHECK(NM_SEQ BETWEEN 1 AND 10) ,
  GENDER VARCHAR2(10),
  CONSTRAINTS check2 CHECK(GENDER IN ('MAN', 'WOMAN'))
);

```

### 2. 테이블 삭제 `DROP`

```SQL
DROP TABLE [스키마.]테이블 명 [CASCADE CONSTRAINTS];
```

### 3. 테이블 수정 `ALTER`
- 칼럼명 변경

```SQL
ALTER TABLE [스키마.]테이블 명 RENAME COLUMN 변경 전 칼럼명 TO 변경 후 칼럼명;
```

- 칼럼 타입 변경
```SQL
ALTER TABLE [스키마.]테이블 명 MODIF 칼럼명 데이터타입;
```

- 칼럼 추가
```SQL
ALTER TABLE [스키마.]테이블 명 ADD 칼럼명 데이터타입
```

- 칼럼 삭제 
```SQL
ALTER TABLE [스키마.]테이블 명 DROP COLUMN 칼럼명;
```

- 제약조건 추가 및 삭제
```SQL
ALTER TABLE [스키마.]테이블 명 ADD CONSTRAINTS 제약조건명 PRIMARY KEY (칼럼명, ...);
```

### 4. 테이블 복사

```SQL
CREATE TABLE [스키마.]테이블명 AS
SELECT 칼럼1, 칼럼2, ...
FROM 복사할 테이블 명
```
