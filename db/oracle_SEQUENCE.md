## 오라클 시퀀스
### 1. 시퀀스란
- 자동으로 순차적으로 증가하는 순번을 반환하는 데이터베이스 객체
- 보통 PK값에 중복값을 방지하기 위해 사용

### 2. 문법
#### 2-1. 시퀀스 생성
```SQL
--문법
CREATE SEQUENCE [시퀀스명]
INCREMENT BY [증감숫자] --증감숫자가 양수면 증가 음수면 감소 디폴트는 1
START WITH [시작숫자] -- 시작숫자의 디폴트값은 증가일때 MINVALUE 감소일때 MAXVALUE
NOMINVALUE OR MINVALUE [최솟값] -- NOMINVALUE : 디폴트값 설정, 증가일때 1, 감소일때 -1028 
                               -- MINVALUE : 최소값 설정, 시작숫자와 작거나 같아야하고 MAXVALUE보다 작아야함
NOMAXVALUE OR MAXVALUE [최대값] -- NOMAXVALUE : 디폴트값 설정, 증가일때 1027, 감소일때 -1
                               -- MAXVALUE : 최대값 설정, 시작숫자와 같거나 커야하고 MINVALUE보다 커야함
CYCLE OR NOCYCLE --CYCLE 설정시 최대값에 도달하면 최소값부터 다시 시작 NOCYCLE 설정시 최대값 생성 시 시퀀스 생성중지
CACHE OR NOCACHE --CACHE 설정시 메모리에 시퀀스 값을 미리 할당하고 NOCACHE 설정시 시퀀스값을 메로리에 할당하지 않음
```

#### 2-2. 시퀀스 조회
```SQL
SELECT EX_SEQ.CURRVAL FROM DUAL --해당 시퀀스 값 조회
SELECT * FROM USER_SEQUENCES  --전체 시퀀스 조회
```

#### 2-3. 시퀀스 수정
```SQL
--문법
ALTER SEQUENCE [시퀀스명]
INCREMENT BY [증가값]
NOMINVALUE OR MINVALUE [최솟값] 
NOMAXVALUE OR MAXVALUE [최대값]
CYCLE OR NOCYCLE [사이클 설정 여부]
CACHE OR NOCACHE [캐시 설정 여부]
```

#### 2-4. 시퀀스 삭제
```SQL
--문법
DROP SEQUENCE [시퀀스명]
```

### 3. 사용 예시
#### 3-1. 테스트 테이블 생성
```SQL
CREATE TABLE EX_TABLE (BOARD_NUM NUMBER(19,6) NOT NULL);
```
#### 3-2. 만들었던 EX_SEQ 시퀀스로 테스트 테이블에 데이터 넣는다.
```SQL
INSERT INTO EX_TABLE(BOARD_NUM) VALUES(EX_SEQ.NEXTVAL);
INSERT INTO EX_TABLE(BOARD_NUM) VALUES(EX_SEQ.NEXTVAL);
INSERT INTO EX_TABLE(BOARD_NUM) VALUES(EX_SEQ.NEXTVAL);
```
#### 3-3. 위에서 만든 테이블 데이터 확인
```SQL
SELECT * FROM EX_TABLE
```

### 4. 시퀀스 사용 예제
```sql
SELECT SEQ_SEQUENCE.NEXTVAL FROM DUAL;
SELECT SEQ_SEQUENCE.CURRVAL FROM DUAL;
```
- `NEXTVAL`: 다음번호 조회
- `CURRVAL`: 현재번호 조회

#### 4-1. `MAX+1`
```SQL
SELECT NVL(MAX(SEQ)+1, 1) FROM EXAM_TABLE;
```
- `MAX+1` >> 코드블럭과 같이 간단하게 사용 가능
- 차이점??
  - `MAX+1`: 중복 사용 가능
  - `시퀀스(Sequence)`: 중복 사용 불가
