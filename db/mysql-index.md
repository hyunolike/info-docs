## MySQL - `index`
> 인덱스 == 정렬 <br>
> (예를들어 '홍길동'이라는 단어를 찾고싶으면 색인페이지에서 '홍'으로 시작하거나 'ㅎ'으로 시작하는 색인을 찾아보면 빠르게 찾을 수 있다.)
- 지정한 칼럼들을 기준으로 메모리 영역에 일종의 __목차__ 생성
- insert, update, delete 의 성능 희생 >> __select__ 의 성능 향상 ✔
- MySQL의 데이터 검색 >> 첫번째 필드부터 차례대로 검색 (데이터 양 많을 수록 검색 시간 증가)
  - 인덱스 사용 시 테이블 전체 읽을 필요 없기에, 검색&질의 처리 속도 증가 ✔

### 1. 실습
- MySQL 테스트 데이터 (DB마다 존재)
  - ![image](https://user-images.githubusercontent.com/61215550/176818264-da7b489e-7344-4246-8149-a62c80b2b500.png)
#### 1.1 테이블 생성 및 테스트 데이터 삽입
```SQL
CREATE TABLE indexTBL (
	frist_name VARCHAR(14),
    last_name VARCHAR(16),
    hird_date DATE
); 

INSERT INTO indextestdb.indexTBL SELECT first_name, last_name, last_update FROM sakila.actor LIMIT 500;
```

#### 1.2 인덱스 X 특정 이름 조회
```SQL
SELECT * FROM indextestdb.indexTBL WHERE frist_name = 'Mary';
```
- ![image](https://user-images.githubusercontent.com/61215550/176818383-6b95d088-da33-4749-9f3f-79c3c7f12384.png)
- 전체 테이블 조회 ㅠ,ㅠ 시간도 오래...
- 심지어 테이블 전체 다 조회...ㅎ
#### 1.3 인덱스 O 특정 이름 조회 (인덱스 생성)
```sql
CREATE INDEX idx_indexTBL_firstname ON indextestdb.indexTBL(frist_name);

SELECT * FROM indextestdb.indexTBL WHERE frist_name = 'Mary';
```
- ![image](https://user-images.githubusercontent.com/61215550/176818945-9912c645-8f06-49bd-920b-09717dae1c9a.png)
- 속도가 어마무시하다 빠르다는 말
- 인덱스 부분만 조회
