## FCM 서버
> [스프링 <--> FCM <--> 안드로이드](https://medium.com/2kyung19/firebase-spring-boot-%EC%97%90%EC%84%9C-android-app%EC%9C%BC%EB%A1%9C-%EC%95%8C%EB%A6%BC-push-%ED%95%98%EA%B8%B0-c4ec80f2dd6d) <BR>
> [참고자료](https://firebase.google.com/docs/cloud-messaging?hl=ko)
- Firebase Cloud Messaging >> 무료로 안정적으로 전송할 수 있는 크로스 플랫폼 메시지 솔루션
- 주요 기능
  - 알림 메시지 / 데이터 메시지 전송
  - 다양한 메시지 타겟팅
  - 클라이언트 앱에서 메시지 전송

### 1. 메시지 유형
- 알림 메시지: 자동으로 SDK 처리 해줌
- 데이터 메시지: 커스텀 키-값 쌍으로 적절한 키 설정 >> (데이터 페이로드) >>클라이언트 앱 
