## 파일 서버
### 파일 서버란
- 파일 서버 >> `Window File Server` `Unix File Server` `Linux File Server`
- `Window File Server` >> `CIFS(Common Internet File System)` 사용해 클라이언트에 스토리지 공유 ⭐
  - 윈도우 탐색기 > 마우스 > 속성 > 공유 = 폴더 공유 ✔
  - 다른 PC에서 네트워크 드라이브 연결 >> 상대방 피시의 스토리지 원격 접속 
- `Unix File Server` `Linux File Server` >> `NFS(Network File System)` 사용 ⭐
- 😁 파일 서버 구축은 OS가 무엇이냐가 중요
- ![image](https://user-images.githubusercontent.com/61215550/171757962-f059f271-7575-4535-b5d5-8d62496b3c48.png)

### `Samba`
- `SMB/CIFS` 네트워킹 프로토콜 다시 구현한 자유 소프트웨어

### `SMB(Server Message Block)`
- 마이크로소프트사 + 인텔 >> 윈도우 시스템이 다른 시스템의 디스크나 프린터와 같은 자원 공유할 수 있도록 개발된 프로토콜

### `CIFS(Common Internet File System)`
- 네트워크를 위한 SMB 파일 공유 프로토콜의 확장된 버전 >> 윈도우와 유닉스 환경을 동시에 지원하는 인터넷의 표준 파일 규약 프로토콜

### `NFS(Network File System)`
- 네트웍을 통한 분산 파일 시스템
- 다른 호스트에 있는 파일 시스템의 일부를 자신의 폴더인 것처럼 마운트하여 사용 가능

