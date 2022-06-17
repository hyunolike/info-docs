## 윈도우 서버 - `jar` 배포
- 크게 2가지 방법 존재
  - `foreground`
  - `background` 

### 1. foreground
- 콘솔창 닫으면 해당 프로세스도 종료되는 방식
- `java -jar JAR-NAME.jar`

### 2. background
- 콘솔창 상관 없이 백그라운드로 실행
- `javaw -jar JAR-NAME.jar`
- 프로세스 종료 방법

```
// javaw 이름으로 실행중인 프로세스를 검색한다
tasklist /svc | findstr javaw 

// 검색된 프로세스의 id값을 이용해 프로세스를 종료한다
taskkill /pid PID /f
taskkill /pid 3778 /f
```
