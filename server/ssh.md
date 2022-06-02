## `SSH` 서버
> [참고자료](https://www.ssh.com/academy/ssh/server)
- `SSH`: 신뢰할 수 없는 네트워크를 통해 두 컴퓨터 간에 데이터를 안전하게 교환하기 위한 프로토콜
  - 전송된 ID, 데이터 및 파일의 개인 정보와 무결성 보호
  - 대부분의 컴퓨터와 거의 모든 서버에서 실행 
- ⭐⭐⭐⭐⭐⭐⭐⭐⭐ `UNIX, Linux, macOS` 시스템에서 __표준__ 으로 제공
- 전세계 데이터 센터의 90%이상 사용

### `SSH` 서버 작동 방식
- `클라이언트 <--> 서버` 모델에서 작동
  - `SSH Client`: 항상 보안 연결 설정을 시작
  - `SSH Server`: 공개 키 제공하여 클라이언트에 자신을 인증

### `Windows 용 SSH` 존재하지 않음 ㅠ,ㅠ
- 가장 심각한 단점
- `SSH Windows Server` >> SSH 서버 설치해야됨! 
  - `Tectia SSH`
  - `Open SSH`
  - `Windows PowerShell` >> [참고 자료](https://docs.microsoft.com/en-us/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7.2)
- `SSH Windows Client` >> 설치해야돼...ㅎ
  - `putty`
  - `filezila`
