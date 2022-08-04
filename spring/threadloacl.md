## Spring 동기, 비동기, 배치 처리시 >> `context` 유지 및 로깅
> [참고자료](https://blog.gangnamunni.com/post/mdc-context-task-decorator/)

### 1. (사전지식) 로깅 시스템 `Correlation id` & `MDC`
> [참고자료](https://bcho.tistory.com/1316)
- (기존) 멀티 쓰레드 >> 각각의 요청 처리 시 / 쓰레들 서로 컨텍스트 바꿔가며 실행 >> 로그 메시지 섞이게 됨 ㅠ,ㅠ
- (개선) 각 요청마다 `ID` 부여 >> 로그 기록 시 묶어서 볼 수 있게됨


|기존|개선 `Correlatoin ID`|
|-----|----------------------|
|![image](https://user-images.githubusercontent.com/61215550/182755788-11a7f962-bda9-4cdd-b8f0-a0d0a238e965.png)|![image](https://user-images.githubusercontent.com/61215550/182755804-3e705772-54f7-4fad-a1ab-b912c50dd1e6.png)|


#### 1.1 `Correlation ID` 구현 방법 >> `ThreadLocal` ✔
- ThreadLocal: 쓰레드의 로컬 컨텍스트 변수 >> Thread 존재하는 한 계속해서 남아있는 변수
  - 쓰레드 안에서 계속 참고해서 쓸수 있는 쓰레드 범위의 **글로벌 변수**

#### 1.2 `MDC` >> `ThreadLocal` 구현의 어려움 해소!! ✔
- `slf4j` `logback` `log4j2` >> `MDC`(Mapped Diagstic Context) 제공
- 단순 CorrelationID 뿐 아닌 map 형식으로 여러 메타 데이타 넣을 수 있음
- ⭐요청마다 >> 다양한 컨텍스트 정보 MDC 저장 >> 로그 출력시 함께 출력하면 더 의미 있는 로그 출력 가능해짐!

