## `MS SQL` 코멘트 생성 및 확인

### 코멘트 생성
```sql
--1. 주석추가 (ADD)
--테이블
EXEC   SP_ADDEXTENDEDPROPERTY 'MS_DESCRIPTION', '테이블설명', 'USER', DBO, 'TABLE',테이블명

--컬럼
EXEC   SP_ADDEXTENDEDPROPERTY 'MS_DESCRIPTION', '컬럼설명', 'USER', DBO, 'TABLE', 테이블명, 'COLUMN', 컬럼명

--2. 주석수정 (UPDATE)
--테이블
EXEC   SP_UPDATEEXTENDEDPROPERTY 'MS_DESCRIPTION', '테이블설명', 'USER', DBO, 'TABLE',테이블명

--컬럼
EXEC   SP_UPDATEEXTENDEDPROPERTY 'MS_DESCRIPTION', '컬럼설명', 'USER', DBO, 'TABLE', 테이블명, 'COLUMN', 컬럼명
```

### 코멘트 확인(조회)
- `fn_listextendedproperty` 함수를 통해 칼럼의 Desription 조회 가능
- `sys.fn_listextendedproperty` `::fn_listextendedproperty` 로도 사용 가능
- sys.fn_listextendedproperty함수는 이하의 장소에 위치해 있습니다.
  - 테이터베이스 > 시스템 테이터베이스 > master > 프로그래밍 기능 > 함수 > 시스템 함수 > 테이블 반환 함수


```sql
-- 테이블 코멘트 조회
SELECT OBJTYPE, OBJNAME, NAME, VALUE 
FROM ::FN_LISTEXTENDEDPROPERTY (NULL, 'SCHEMA', 'DBO', 'TABLE', '테이블명', DEFAULT, DEFAULT);

-- 칼럼 코멘트 조회
SELECT OBJTYPE, OBJNAME, NAME, VALUE 
FROM ::FN_LISTEXTENDEDPROPERTY(NULL, 'SCHEMA', 'DBO', 'TABLE', '테이블명', 'COLUMN', DEFAULT);
```
