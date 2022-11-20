## HTTP Live Streaming - `2012년 자료`
> [참고자료](https://d2.naver.com/helloworld/7122)
- ✅ 전통적인 프로토콜 `RTSP` >> 라이브 스트리밍
  - 도입 비용 높다 ㅠ,ㅠ 
  - 방화벽 환경에서 서비스 원할하게 이뤄지지 않음 ㅠ,ㅠ
- 🎉 `HTTP` >> Apple이 만든 HLS(HTTP Live Streaming) >> 기존 프로토콜의 단점을 해결?!

### 1. 라이브 스트리밍이란
- 텔레비전 생방송처럼 촬영한 정보를 실시간으로 사용자의 동영상 플레이어로 보내 재생하도록 하는 방식
- 비디오 + 오디오 >> 실시간으로 인코딩해 많은 사용자에게 동시에 보낼 수 있어야 함
- 라이브 스트리밍 위한 전통적인 프로토콜 - 서로 다른 네트워크 연결을 통해 데이터 교환 >>  NAT(Network Address Translator) 많이 쓰는 환경에서는 서비스 ㅠ,ㅠ 어려움
  - `RTSP (Real-Time Streaming Protocol) / RTP (Real-time Transport Protocol)`
  - `RTMP (Real-Time Messaging Protocol)`
- ✅ 해당 프로토콜 사용하는 서버 >> 기능이 많은 만큼 도입 비용 상대적을 높음! 
  - 영상 데이터의 전송
  - 동영상에 대한 정보 분석 / 전송 규격에 맞도록 동영상 파일을 읽어서 변형하는 기능
### 2. 비교
|HLS|기존|
|--|---|
|![image](https://user-images.githubusercontent.com/61215550/202886533-ca377b89-fd06-4624-9f1d-f5dddcd5e6cd.png)|![image](https://user-images.githubusercontent.com/61215550/202886537-ced2689e-3f1e-442b-a75f-d5cc38616c0c.png)|
