## ์ค๋ผํด ๋ทฐ `VIEW`
> ๐ถ ๋ณต์กํ ์ฟผ๋ฆฌ ๋ฐ๋ณตํด์ ์ฐ์ง ์๊ณ  ๋ง์น ํจ์์ ๋ก์ง ๋ด์๋์ ๊ฒ์ฒ๋ผ ๋ณต์กํ ์ฟผ๋ฆฌ๋ก ๊ฐ์์ ํ์ด๋ธ๋ก ๋ง๋ค์ด ๋์
> ํ์ํ ๋ฐ์ดํฐ๋ค๋ง ์กฐ์ํ  ์ ์๊ฒ ํ๋ ๊ฑฐ์ผ!!! โญ
- ๋ทฐ๋ ์ค์  ๋ฐ์ดํฐ๊ฐ ์ ์ฅ๋์ด์์ง ์์ง๋ง `DML` ์์์ด ๊ฐ๋ฅํ __๊ฐ์์ ํ์ด๋ธ__ โ
  - `DML` (๋ฐ์ดํฐ ์กฐ์์ด: `SELECT` `INSERT` `UPDATE` `DELETE`
- ์์ฃผ ์กฐํํ๋ ๋ฐ์ดํฐ๋ค!!!
  - ์ฌ๋ฌ ํ์ด๋ธ ์กฐ์ธ์ฌ์ฉํด ๊ฐ์ ธ์ค๋ ๋ณต์กํ ์ฟผ๋ฆฌ ์ฌ์ฉํ  ๋
  - ์ด๋ฐ ๊ฒฝ์ฐ ์ฟผ๋ฆฌ๋ก ๋ทฐ ๋ง๋ค์ด ๋๊ณ  ์ฌ์ฉ!!
- ๋ณด์์ ์ ๋ฆฌ!!!
  - ํ์ด๋ธ์ ๋ฐ์ดํฐ ๋ธ์ถ์ํค๊ณ  ์ถ์ง ์์ ๋, ๋ทฐ๋ฅผ ์ฌ์ฉํ์ฌ __๋ณด์ฌ์ค ๋ฐ์ดํฐ__ ๋ง ๋ทฐ๋ก ์ฌ์ฉ !!
  
### 1. ๋ฌธ๋ฒ

```SQL
CREATE [OR REPLACE] [FORCE|NOFORCE] VIEW ๋ทฐ ์ด๋ฆ
  [(column_aliases)]
AS
  SELECT ๋ฌธ
  [WITH READ ONLY]
  [WITH CHECK OPTION [CONSTRAINT ์ ์ฝ์กฐ๊ฑด๋ช]]
```
- `OR REPLACE`: ํด๋น ๊ตฌ๋ฌธ์ ์ฌ์ฉํ๋ฉด ๋ทฐ๋ฅผ ์์ ํ  ๋ DROP ์์ด ์ฌ์ฉ ๊ฐ๋ฅ
- `FORCE`: ๋ทฐ๋ฅผ ์์ฑํ  ๋ ์ฟผ๋ฆฌ๋ฌธ์ ํ์ด๋ธ, ์นผ๋ผ, ํจ์ ๋ฑ์ด ์กด์ฌํ์ง ์์๋ ์์ฑ ๊ฐ๋ฅ
- `NOFORCE`: ๋ทฐ๋ฅผ ์์ฑํ  ๋ ์ฟผ๋ฆฌ๋ฌธ์ ํ์ด๋ธ, ์นผ๋ผ ํจ์ ๋ฑ์ด ์กด์ฌํ์ง ์์ผ๋ฉด ์์ฑํ์ง ์์
- `column_aliases`: SELECT ์นผ๋ผ ๋ณ์นญ ๋ฏธ๋ฆฌ ์ง์  ๊ฐ๋ฅ
- `WITH READ ONLY`: SELECT ๋ง ๊ฐ๋ฅ! (INSERT, UPDATE, DELETE ๋ถ๊ฐ๋ฅ)
- `WITH CHECK OPTION`: WHERE ์ ์ ์กฐ๊ฑด์ ํด๋นํ๋ ๋ฐ์ดํฐ๋ง ์ ์ฅ, ๋ณ๊ฒฝ ๊ฐ๋ฅ

#### 1-1. ์์ฑ
- ๋จ์ ๋ทฐ ์์ฑ

```SQL
CREATE OR REPLACE VIEW V_EXP
AS
  SELECT NAME, JOB, AGE
  FROM T_EXP
  ;
```
- ๋ณตํฉ ๋ทฐ ์์ฑ

```SQL
CREATE OR REPLACE VIEW V_EXP
AS
  SELECT T.NAME, T.JOB, T.AGE, TO_CHAR(A.HIREDATE, 'YYYY-MM-DD') AS HIREDATE
  FROM T_EXP T, K_EXP K
  WHERE T.DEP = K.DEP
  ;
```
#### 1-2. ๋ทฐ ์นผ๋ผ ์ฝ๋ฉํธ ์ถ๊ฐ
```SQL
COMMENT ON COLUMN V_EMP.EMPNO IS '์ฌ์ ๋ฒํธ';
```

#### 1-3. ๋ทฐ ์ญ์ 
```SQL
DROP VIEW ๋ทฐ ์ด๋ฆ 
```

### 3. ์์

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
FROM ์คํค๋ง.ํ์ด๋ธ ๋ช ST
	INNER JOIN CDM.SHIPPING_INFO SI ON ST.INFO_ID = SI.ID
WHERE ST.TRY_STATUS = 'REQUEST'
	AND TO_CHAR(ST.CREATED, 'YYYYMMDD') < TO_CHAR(CURRENT_DATE, 'YYYYMMDD')
	AND ASP_ID != '000138000000000'
WITH READ ONLY;
```

