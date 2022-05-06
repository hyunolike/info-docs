## `MSSQL` docker 설치
- [참고 자료1](https://www.lesstif.com/dbms/docker-ms-sql-server-113347394.html)
- [참고 자료2](https://oingdaddy.tistory.com/285)
- [`docker` mssql](https://hub.docker.com/_/microsoft-mssql-server?tab=description) ✔

### 1. Docker MSSQL 설치 - `pull`
- `docker pull mcr.microsoft.com/mssql/server:2017-latest`
- ![image](https://user-images.githubusercontent.com/61215550/167046901-10664a1c-f734-4163-8114-f070e0e09cc4.png)

### 2. Docker MSSQL 설치 - `run`
- `docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=<your password>' -p 1433:1433 --name <mssql-server> -d mcr.microsoft.com/mssql/server:2017-latest`
- ![image](https://user-images.githubusercontent.com/61215550/167047090-8919fe48-fd12-406b-a99a-5a46cc5715bd.png)

### 3. 현재 컨테이너 조회 - `ps`
- `docker ps -a`
- ![image](https://user-images.githubusercontent.com/61215550/167047107-0c38f070-bef8-40ea-8c0c-9f00d7c320d6.png)

### 4. SA 계정 암호 변경
> 📌 여기서 비밀번호는 아무거나? 해준다!
- `docker exec -it <mssql-server> /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P  "<YourStrong@Passw0rd>" `
- `T-SQL` 콘솔에서 다음 명령어 실행해서 SA 암호 변경해준다!
```SQL
ALTER LOGIN SA WITH PASSWORD="<YourNewStrong@PasswOrd>";
GO
```
### 5. container 진입
- `docker exec -it <mssql-server> "bash"`

### 6. MSSQL 접속
- `/opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P "<your password>"`
- ![image](https://user-images.githubusercontent.com/61215550/167047408-497506a3-9c5f-48f1-a3df-091cebfdc4e0.png)

### 6. DB 생성
```SQL
CREATE DATABASE <DB명>
GO

USE <DB명>
```

### 7. 사용자 계정 생성
```SQL
CREATE LOGIN <USER> WITH PASSWORD='<USER PASSWORD>'
GO

CREATE USER <USER> FOR LOGIN <USER>;
GO
```
- ![image](https://user-images.githubusercontent.com/61215550/167047639-5b043fb0-7416-42fa-b602-ea5fb8fbf8e0.png)

### 8. 계정 권한 할당
```SQL
exec sp_addrolemember 'db_owner', <USER>;
```
- ![image](https://user-images.githubusercontent.com/61215550/167047651-aa82b75a-a3f6-4cc3-9dde-8783e0d8f59b.png)

---

### 9. 접속 확인 😁
> 여기서 sa 기본 로그인으로 해야지 테이블 수정 및 생성 모두 가능해짐!! ⭐
- ![image](https://user-images.githubusercontent.com/61215550/167052798-755cd3cc-bd18-40d4-ae16-3597d60e8d96.png)

