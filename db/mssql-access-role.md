# `MSSQL` 인증 엑세스 > 서버 수준 역할
> [참고자료](https://learn.microsoft.com/ko-kr/sql/relational-databases/security/authentication-access/server-level-roles?view=sql-server-ver16)

## 개요
- 서버에 대한 사용 권한 관리
- 그룹화한 보안 주체
- `sql server 2022` > 10개의 추가 서버 역할 제공
  - `##MS_` 접미사 & `##` > 사용자 정의 일반 보안 주체 및 지정 서버 역할 구별 가능
- 😛 계층적 구성
  -  `##MS_DatabaseConnector##`: 멤버 + 모든 데이터베이스 connect 권한 부여 / 개별 데이터베이스 > 사용자 계정 존재 필수
  - `##MS_ServerStateReader##`: VIIEW SERVER STATE 권한 보유
- 서버 수준 보안 주체(SQL Server 로그인, Windows 계정 및 Windows 그룹) 서버 수준 역할 추가 가능
- 고정 서버 역할의 각 멤버 > 동일한 역할 > 다른 로그인 추가 가능
- 사용자 정의 서버 역할의 멤버 > 다른 서버 주체 추가 가능

## 고정 서버 수준 역할
- `2022`버전 이전 도입 서버 수준 역할 주의 사항
  - `Azure SQL Database` `Azure Synapse Analytics` 사용 불가
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/0407c030-873e-4f8d-bb36-6a1353538fb0)![image](https://github.com/hyunolike/info-docs/assets/61215550/cacaba74-1dc7-43de-9aef-ceaaf95baf22)



 
