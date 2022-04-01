## 인덱스(Index)
- 데이터베이스 테이블에 존재하는 데이터 빨리 찾기 위한 용도의 데이터베이스 객체이며 일종의 색인기술
- 어떤 데이터가 어느 위치에 있다는 정보를 가진 __주소록__ 같은 개념
- 빠르게 쿼리 검색을 위해 사용
- __오라클 select 원리__
  1. select 쿼리 
  2. 메모리의 데이터베이스 버퍼 캐시 확인
  3. 버퍼 캐시(자주 사용하는 테이블 캐싱되어 있음 있을 경우 바로 찾아 출력
  4. 없을 경우 하드 디스크에 있는 데이터 파일에서 데이터 찾기
  - ✔ 인덱스 사용 시, 위 과정 거치지 않고 바로 주소 찾아감!! 
### 인덱스 종류
|종류|설명|
|------|------|
|`B-TREE index`|- OLTP(Online Transaction Processing) 실시간 트랜잭션 처리<br>- 실시간으로 데이터 입력, 수정 일어나는 환경에서 많이 사용|
|`BITMAP index`|- OLAP(Online Analytical Processing) 온라인 분석 처리<br>- 대량의 데이터 한꺼번에 입력 후 주로 __분석, 통계__ 정보 출력할 때 많이 사용<br>- 데이터 값 종류가 적고 동일한 데이터가 많을 경우에 사용|
#### `B-TREE index`
- `B`: binary, balance 약자 
- ![image](https://user-images.githubusercontent.com/61215550/161192636-e49c27a3-3484-4e6c-9409-874bf609844b.png)

```
    ROOT block(branch block에 대한 정보)

     |

  Branch Block(Left Block에 대한 정보)

     |

    Leaf Block(실제 데이터들의 주소)
```
- 종류

|종류|설명|
|-----|------|
|`Unique index`|- 인덱스 안에 있는 칼럼 key값에 중복되는 데이터 없다.(성능 좋음)<br>- Unique 제약조건과 유사|
|`Non Unique index`|중복되는 데이터 들어가야 하는 경우(key로 지정한 필드의 중복된 값 들어갈 수 있다)|
|`FBI index`(Function Based Index)<br>함수기반 인덱스|- 인덱스는 __where__ 절에 오는 조건 칼럼이나 조인에 쓰이는 칼럼 만들어야 됨|
|`Descending index`|내림차순으로 인덱스 생성|
|`Composite index`(결합 인덱스)|인덱스 생성시에 두 개 이상의 칼럼을 합쳐서 인덱스를 생성하는 인덱스<br>- 주로 where절 조건이 되는 칼럼이 2개 이상으로 and로 연결되는 겨우 사용|


#### `BITMAP index`
- 데이터 값 종류가 적고 동일한 데이터가 많을 경우 많이 사용 
- 어떤 데이터가 어디에 있다는 지도정보(MAP)를 Bit로 표현 ✔
- 데이터 존재하는 곳 `1` 없는 곳 `0` 
  - 정보를 찾을 떄 `1`인 값만 찾게 된다! 

### 인덱스 설정 방법
- 인덱스 설정

```sql
CREATE INDEX [인덱스 명] ON [테이블 명]
(칼럼1, 칼럼2)
;
```
- UNIQUE 인덱스 설정

```sql
CREATE UNIQUE INDEX [인덱스 명] ON [테이블 명]
(칼럼1, 칼럼2)
;
```
- PK 인덱스 설정

```sql
ALTER TABLE [테이블 명] ADD (
  CONSTRAINT [PK 설정할 인덱스명]
  PRIMARY KEY(칼럼1, 칼럼2, 칼럼3)
);
```



