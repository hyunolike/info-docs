## mongoDB
> [참고자료](https://velog.io/@ckstn0777/MongoDB%EB%9E%80)
![image](https://user-images.githubusercontent.com/61215550/180920258-b6b18934-3560-43a5-84ea-eb33b418d830.png)

### 1. 먼저 `SQL` VS `NoSQL`
- SQL
  - ... 기본이니까 넘어가기
- NoSQL
  - 덜 제한적인 일관성 모델을 이용하는 데이터의 저장 및 검색을 위한 매커니즘 제공
  - 빅데이터와 실시간 웹 애플리케이션의 상업적 이용에 사용
  - SQL 계열 쿼리 언어를 사용할 수 있다는 사실 강조한다는 면에서 `Not only SQL`
 
 #### 1.2 NoSQL 분류
- `Wide Columnar Store`: 카산드라
- `Document Store`: MongoDB ✔
- `Key-Value Store`: 다이나모, 레디스
- `Graph Store`: Neo4j

### 2. MongoDB
- ![image](https://user-images.githubusercontent.com/61215550/180920651-fea323f8-1f8b-44f4-a439-3e40c29744d7.png)
- C++ 작성된 오픈소스 `문서지향` 크로스 플랫폼 데이터베이스
#### 2.1 `Document`
```
{
    "_id": "5f2ad6b54866e5109dd2367b"
    "username": "홍길동",
    "hashedPassword": "비밀번호",
}
```
- 위와 같은 키, 벨류로 이루어진 데이터 구조 >> `Document`
- `_id` 값은 유일 / `Primary Key`랑 동일한 개념
- ![image](https://user-images.githubusercontent.com/61215550/180920683-a9462a45-2a3e-485a-9a5b-3f89662be23d.png)

#### 2.2 `Collection`
- Document의 그룹 / RDBMS로 따지면 `Table`과 비슷한 개념!
- 스키마를 가지고 있지 않음!!

#### 2.3 `Database`
- Collections 들의 물리적인 컨테이너이자 가장 상위 개념 / RDBMS에서의 Database와 동일한 개념
