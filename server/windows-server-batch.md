## 윈도우 서버 배치 파일 (배포) 예시
> [참고 자료](https://mchch.tistory.com/94)
```bat
@echo off

set serverPort=포트번호
set serverPortPID=

netstat -ano | findstr %serverPort%

if %ERRORLEVEL% equ 0 (
ECHO "DELETE-SERVICE after START-SERVICE running ..."
GOTO :DELETE-SERVICE
) else (
ECHO "START-SERVICE ..."
GOTO :START-SERVICE
)

:DELETE-SERVICE
.\DEPLOY\[서비스 명].exe uninstall
for /f "tokens=5 delims= " %%a IN ('netstat -ano ^| findstr %serverPort%') do set result=%%a
taskkill /f /pid %result%
GOTO :START-SERVICE

:START-SERVICE
.\DEPLOY\[서비스 명].exe install
net start [서비스 명]
```
