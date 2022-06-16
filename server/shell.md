## `shell`
> [참고 자료](https://velog.io/@swhan9404/%EC%89%98-%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EB%B0%B0%EC%B9%98%ED%8C%8C%EC%9D%BC-%EB%A7%8C%EB%93%A4%EA%B8%B0)
- 사용자로부터 받은 명령을 kernel 이해하도록 해석하여 전달하는 명령어 해석기
- 사용자와 운영체제 사이를 `Interface` 시키는 하나의 유틸리티 프로그램
- `shell`: 사용자가 입력한 명령 라인을 읽어들여 해석하고 리눅스 시스템을 통해서 명령 라인이 실행되게 하는 `Command Interpreter`(명령 한줄 씩 해석)

### 1. 쉘 종류
- 리눅스
  - `/bin/sh`: 최초로 만들어진 표준 쉘 / 복구 모드에 사용 / 우분투에서 /bin/sh는 dash로 링크 걸려짐
  - `/bin/bash`: 리눅스에서 가장 대표적으로 사용하는 쉘 / 기능이 많은 대신 dash보다 느림
- 윈도우
  - `cmd`: 모두가 알고있는 dos와 동일한 구문과 기능을 베이스로하는 간단하고 기본적인 쉘
  - `PowerShell`: MS가 이를 발전시켜 __.net 2.0__ 기반으로 설계한 뉴페이스 쉘

### 2. 정리
- ✔과정: `kernel` >>> `shell` >>> `shell programing`
  - `kernel`: 운영 체제의 핵심이 되는 프로그램
  - `shell`: 커널에 명령을 전달하는 프로그램
  - `shell programing`: 쉘에 직접 명령어 날리는 것

