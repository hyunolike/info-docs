## `mssql`
> NVARCHAR, VARCHAR 

### 1. `SQL Server JDBC Driver`
> [참고 자료](https://techblog.woowahan.com/2605/)
- String type의 parameter를 기본적으로 `NVARCHAR`로 매핑 ⭐
- 그렇기에 String type을 `VARCHAR`로 매핑하고 싶다면 `sendStringParametersAsUnicode=false` 추가 - url에다가

#### 문제점
- `SQL Server JDBC Driver` >> String 파라미터를 모두 `NVARCHAR` 로 매핑
- 위의 문제로 `VARCHAR` 칼럼 조회 조건 사용 시, 해당 칼럼에 대한 INDEX 모두 무시 ㅠ,ㅠ >> 성능 저하 발생 
- 규모가 큰 서비스일 수록 성능 저하의 영향을 크게 받음 >> `MSSQL은 DATATYPE에 대한 우선순위` 존재!! - [데이터 형식 우선 순위](https://docs.microsoft.com/ko-kr/sql/t-sql/data-types/data-type-precedence-transact-sql?view=sql-server-2017)
- ![image](https://user-images.githubusercontent.com/61215550/168726509-ddb2e2c1-5da2-4c30-80dd-5c8823cd2efb.png)

#### 해결
- `sendStringParametersAsUnicode=false` 추가! >> String 파라미터 모두 `VARCHAR` 타입으로 매핑 ⭐

### 2. MSSQL 데이터 타입 이슈 
- 데이터타입을 지정하지 않고 그냥 값을 넘기면 `MSSQL`의 내부 규칙에 의해 __NVARCHAR__ type으로 넘어가게됨
#### 해결
1. 타입 캐스팅
2. `sendStringParametersAsUnicode=false`

### 3. 다국어 문제 ✔
> [참고 자료](https://hermeslog.tistory.com/527)
- 한글 사용 시 


|설정해야 할거|설정 값|
|------------|----------|
|Collation|`Korean_Wansung_CI_AS`|
|DBCP|`sendStringParametersAsUnicode=false`|

#### 주의점
- Collation `SQL_Latin1_General_CP1_CI_AS` 설정 시
  - `sendStringParametersAsUnicode=false` 사용하면 물음표 `?` 로 저장
- Collation 이 "Korean_Wansung_CI_AS" 이더라도, Server Collation 이 "SQL_Latin1_General_CP1_CI_AS" 인 경우 Temp Table 생성 시 "SQL_Latin1_General_CP1_CI_AS" 로 생성
