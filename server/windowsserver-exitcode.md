## `Windows` Errorlevel and Exit codes
> [참고 자료](https://ss64.com/nt/errorlevel.html)

### 1. 오류 수준 감지
- 오류 수준 감지 방법 크게 2가지
  - `IF ERRORLEVEL ...`
  - `%ERRORLEVEL%`
#### 1.1 `IF ERRORLEVEL ...` 
- `ERRORLEVEL 0`: 오류 수준 0, 1 또는 5 또는 64인지 여부관계 없이 `TRUE` 반환

#### 1.2 `%ERRORLEVEL%`
- 오류 수준의 기본적인 확인 방법
```
IF %ERRORLEVEL% NEQ 0 Echo An error was found
IF %ERRORLEVEL% EQU 0 Echo No error found

IF %ERRORLEVEL% EQU 0 (Echo No error found) ELSE (Echo An error was found)
IF %ERRORLEVEL% EQU 0 Echo No error found || Echo An error was found
```

