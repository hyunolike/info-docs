## 방화벽 확인 `telnet`
> [참고 자료](https://uutopia.tistory.com/4) <BR>✔ `PING` 대신 `telnet` 사용하자!!(네트워크 공격의 위험성) ㅠ,ㅠ
- 실무에서의 방화벽
  - 송신서버 `OUTBOUND`
  - 수신서버 `INBOUND`
### `telnet` >> 통신 여부 확인
- 본래 원격지의 호스트에 접속해 컨트롤 하는 것이 목적 >> 패킷을 암호화 하지 않고 취약하므로 원격 컨트롤 보다는 단순히 __통신 가능 여부__ 확인하는 목적 ⭐
- 윈도우에서의 사용 방법
  - `Windows 기능 켜키/끄기` > 텔넷 클라이언트 활성화 ✔
- 명령어 `telnet 서버ip [포트번호]`

### 추가
- `netstat`
  - 네트워크 연결 상태 확인
  - 명령어 `netstat -an|find "IP:PORT"`
- `telnet` + `netstat`
  - 특정 원격서버와의 네트워크 통신 상태 간단하게 확인
- 용어
  - `SYN-SENT`: 신호 보냄(상태가 지속되다 연결이 끊긴경우 송신은 성공했지만 수신서버의 INBOUND 방화벽 막혀있을 확률 높음)
  - `ESTABLISHED`: 연결 성공  
- `telnet` >> 바로 연결 실패하여 결과확인 불가할 경우 송신서버의 OUTBOUND 방화벽 막혀있을 확률 높음