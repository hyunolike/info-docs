## 배치 파일(일괄처리용 파일) / 도스 명령어
> [참고 자료](https://m.blog.naver.com/novajini/220158416308) <BR>
> [참고 자료 - 배치 파일](http://www.dreamy.pe.kr/zbxe/CodeClip/6383)
- ✔ 도스 상태에서 지원되는 기본적인 배치 명령어

### 1. 핵심 배치 파일 명령어
#### 1.1 `ECHO`
- 배치 파일 내 명령어의 이름을 보여주거나 감추는 기능 수행
- `토글` 처럼 동작
```SHELL
ECHO ON or ECHO OFF
```

#### 1.2 `REM`
- 주석
- 일반적으로 배치 파일 작성자, 작성 날짜, 사용 목적 등을 기술
```
REM [설명]
```

### 1.3 `PAUSE`
- 처리 중인 배치 파일을 멈추고 사용자에게 조건적인 메시지를 보여줌
- 화면을 사용자가 읽기 편하게 잡아놓기 위해 사용 되거나
- 다른 준비 작업을 위해 약간의 여유 주기 위해 사용
```
PAUSE [MESSAGE] 
```

### 1.4 `FOR`
- 일종의 반복문
```
FOR %%변수명 IN (SET) DO Command
FOR /f "tokens=5 delims= " %%a IN ('netstat -ano ^| findstr %serverPort%') DO set result=%%a ✔ 예시
```
- `(SET)`: 범위를 알려주는 것

### 1.5 `GOTO`
- 조건에서 만족하면 지정된 레이블로 제어를 옮겨 주는 기능 수행
- 레이블명은 `:` 앞에 추가후 작성
