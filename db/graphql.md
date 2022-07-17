## GraphQL
> [참고자료](https://tech.kakao.com/2019/08/01/graphql-basic/) <br>
> [공식문서](https://graphql.org/)

### 1. GraphQL(이하 gql)이란 >> 예시 피자 집 주문!!
- Structed Query Language(이하 sql)와 마찬가지로 쿼리 언어
  - ggl과 sql은 언어적 구조 차이 매우 큼 ✔

|`sql`|`gql`|
|----|----|
|__데이터베이스 시스템__ 에 저장된 데이터 효율적으로 가져오는 것 목적|__웹 클라이언트__ 가 데이터를 서버로부터 효율적으로 가져오는 것 목적|
|sql의 문장은 주로 **백엔드 시스템** 에서 작성|gql 문장은 주로 **클라이언트 시스템**에서 작성하고 호출|

- `sql` 
```sql
SELECT plot_id, species_id, sex, weight, ROUND(weight / 1000.0, 2) FROM survey;
```
- `gql`
```gql
{
  hero {
    name
    friends {
      name
    }
  }
}
```

### 2. 비교 `REST API` VS `GraphQL`
- `ggl` 한번의 네트워크로 처리 가능 ✔
- ![image](https://user-images.githubusercontent.com/61215550/179382244-e4c1d8c4-8a98-4b59-9a25-06bb01df1b52.png)
- ![image](https://user-images.githubusercontent.com/61215550/179382472-43cf32f6-8c07-4d26-9653-ccfcd265c9bb.png)

|`REST API`|`GraphQL`|
|-------------|-------------|
|메소드+uri 조합 >> 에측 가능하고 일정한 정보와 작업 요청 <br>✔ 버튼마다 나오는 것이 확실한 자판기 처럼!!!|✔피자 주문처럼 내가 원하는 것만 주문 가능!!<br> ⭐`body`의 주문서로 주문 가능해!!<br> **여러 depth의 정보**를 한번의 요청으로 받아올수 있다|
|필요 없는 정보까지 다 받는다는 단점 ㅠ,ㅠ 결과적으로 1이상의 요청을 보내야돼||

### 3. GraphQL 구조
#### 3.1 쿼리/뮤테이션(query/mutation)
> 개념적 규약 정해놓은 것
- 쿼리: 데이터 Read
- 뮤테이션: C,U,D

#### 3.2 스키마/타입(schema/type)
- gql 스키마 작성 >> C, C++의 헤더파일 작성에 비유
```gql
type Character {
  name: String!
  appearsIn: [Episode!]!
}
```

#### 3.3 리졸버(resolver)
- gql은 sql과 달리 데이터를 가져오는 구체적인 과정을 직접 구현!!
- resolver: 데이터 가져오는 구체적인 과정
  - 데이터베이스, 일반 파일, http/SOAP 네트워크 프로토콜 활용 원격 데이터 >> 모두 가져오기 가능 ⭐

#### 3.4 인트로스펙션(introspection)
- 기존 서버-클라이언트 협업 방식 >> 연동규격서(api 명세서) 주고 받는 절차 반드시 필요

### 4. GraphQL 활용 도와주는 다양한 라이브러리들
- `gql`는 쿼리 언어 >> 이것 만으로는 아무것도 할 수 없다
- `gql` 자체 >> 개발언와 + 사용 네트워크 완전히 독립적
- 라이브러리 종류: 릴레이(Relay), 아폴로(Appollo GraphQL) ✔
- ![image](https://user-images.githubusercontent.com/61215550/179382830-a6e74d3b-398a-48d7-b0ab-5555eae2e0d1.png)

