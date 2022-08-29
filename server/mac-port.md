## 맥북 포트 확인 및 저장 방법
- 쉘에서 포트 목록 확인
  - `sudo lsof -PiTCP -sTCP:LISTEN`
- 특정 포트 찾아 포트 닫고 싶으면 PID 찾아내기
  - `sudo lsof -i :8080`
- 포트 죽일래
  - `sudo kill [PID NUMBER] PID`
