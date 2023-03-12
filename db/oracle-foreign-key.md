## 오라클 제약조건
> [참고자료](https://mine-it-record.tistory.com/45)
- FK 정의된 테이블 >> 자식 테이블
- PK 존재하는 테이블 >> 부모 테이블
- 부모 테이블의 PK 칼럼에 존재하는 데이터만 자식 테이블에 입력 가능
- 부모 테이블은 자식의 데이터나 테이블이 삭제된다고 영향 받지 않음
- 참조하는 데이터 칼럼과 데이터 타입은 반드시 일치

### 구문
```sql
constraint [제약조건 명] foreign key([칼럼명])
  references [참조할 테이블 이름]([참조할 칼럼])
  [on delete cascade | on delete set null]
```

### 제약조건
> [참고자료](https://mine-it-record.tistory.com/39)
- ✅ 데이터의 무결성을 지키기 위한 제한된 조건
  - 테이블이나 속성에 부적절한 데이터가 들어오는 것을 사전에 차단하도록 정해 놓은 것

#### 종류
- `NOT NULL`
- `UNIQUE`
- `CHECK`
- `PRIMARY KEY`
- `FOREIGN KEY`
- `DEFAULT`

#### 제약조건 삭제
```sql
alter table [테이블명] drop constraint [제약조건명]
```
