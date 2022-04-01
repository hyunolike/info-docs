## 오라클 뷰 `VIEW`
> 🎶 복잡한 쿼리 반복해서 쓰지 않고 마치 함수에 로직 담아놓은 것처럼 복잡한 쿼리로 가상의 테이블로 만들어 놓아
> 필요한 데이터들만 조작할 수 있게 하는 거야!!! ⭐
- 뷰는 실제 데이터가 저장되어있지 않지만 `DML` 작업이 가능한 __가상의 테이블__ ✔
  - `DML` (데이터 조작어: `SELECT` `INSERT` `UPDATE` `DELETE`
- 자주 조회하는 데이터들!!!
  - 여러 테이블 조인사용해 가져오는 복잡한 쿼리 사용할 때
  - 이런 경우 쿼리로 뷰 만들어 놓고 사용!!
- 보안에 유리!!!
  - 테이블에 데이터 노출시키고 싶지 않을 때, 뷰를 사용하여 __보여줄 데이터__ 만 뷰로 사용 !!
  
### 1. 문법

```SQL
CREATE [OR REPLACE] [FORCE|NOFORCE] VIEW 뷰 이름
  [(column_aliases)]
AS
  SELECT 문
  [WITH READ ONLY]
  [WITH CHECK OPTION [CONSTRAINT 제약조건명]]
```
- `OR REPLACE`: 해당 구문을 사용하면 뷰를 수정할 때 DROP 없이 사용 가능
- `FORCE`: 뷰를 생성할 때 쿼리문의 테이블, 칼럼, 함수 등이 존재하지 않아도 생성 가능
- `NOFORCE`: 뷰를 생성할 때 쿼리문의 테이블, 칼럼 함수 등이 존재하지 않으면 생성하지 않음
- `column_aliases`: SELECT 칼럼 별칭 미리 지정 가능
- `WITH READ ONLY`: SELECT 만 가능! (INSERT, UPDATE, DELETE 불가능)
- `WITH CHECK OPTION`: WHERE 절의 조건에 해당하는 데이터만 저장, 변경 가능

#### 1-1. 생성
- 단순 뷰 생성

```SQL
CREATE OR REPLACE VIEW V_EXP
AS
  SELECT NAME, JOB, AGE
  FROM T_EXP
  ;
```
- 복합 뷰 생성

```SQL
CREATE OR REPLACE VIEW V_EXP
AS
  SELECT T.NAME, T.JOB, T.AGE, TO_CHAR(A.HIREDATE, 'YYYY-MM-DD') AS HIREDATE
  FROM T_EXP T, K_EXP K
  WHERE T.DEP = K.DEP
  ;
```
#### 1-2. 뷰 칼럼 코멘트 추가
```SQL
COMMENT ON COLUMN V_EMP.EMPNO IS '사원 번호';
```

#### 1-3. 뷰 삭제
```SQL
DROP VIEW 뷰 이름 
```

### 3. 예시

```SQL
  CREATE OR REPLACE FORCE EDITIONABLE VIEW "CDM"."VIEW_BATCH_CANDIDATE" ("TRY_ID", "INFO_ID", "CUSTOMER_NAME", "CUSTOMER_MPN", "USER_ID", "LOGIN_ID", "ASP_ID", "BASE_ADDRESS", "DETAIL_ADDRESS", "ZIP_CODE", "ZIP_CODE_DELIMETER", "PRODUCT_ID", "PREV_PRODUCT_ID", "REQUESTOR", "TRY_REASON", "SENT_CARD_NO", "CARD_TYPE", "TRY_CREATED", "TRY_UPDATED") AS 
  SELECT
		ST.ID AS TRY_ID,
		SI.ID AS INFO_ID,
		SI.CUSTOMER_NAME AS CUSTOMER_NAME,
		SI.CUSTOMER_MPN AS CUSTOMER_MPN,
		SI.USER_ID AS USER_ID,
		SI.LOGIN_ID AS LOGIN_ID,
		SI.ASP_ID AS ASP_ID,
		SI.BASE_ADDRESS AS BASE_ADDRESS,
		SI.DETAIL_ADDRESS AS DETAIL_ADDRESS,
		SI.ZIP_CODE AS ZIP_CODE,
		SI.ZIP_CODE_DELIMETER AS ZIP_CODE_DELIMETER,
		SI.PRODUCT_ID AS PRODUCT_ID,
		SI.PREV_PRODUCT_ID AS PREV_PRODUCT_ID,
		ST.REQUESTOR AS REQUESTOR,
		ST.TRY_REASON AS TRY_REASON,
    ST.SENT_CARD_NO AS SEND_CARD_NO,
    ST.CARD_TYPE AS CARD_TYPE,
		ST.CREATED AS TRY_CREATED,
		ST.UPDATED AS TRY_UPDATED
FROM 스키마.테이블 명 ST
	INNER JOIN CDM.SHIPPING_INFO SI ON ST.INFO_ID = SI.ID
WHERE ST.TRY_STATUS = 'REQUEST'
	AND TO_CHAR(ST.CREATED, 'YYYYMMDD') < TO_CHAR(CURRENT_DATE, 'YYYYMMDD')
	AND ASP_ID != '000138000000000'
WITH READ ONLY;
```

