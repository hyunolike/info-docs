## `RollingFileAppender`
> [참고 자료](https://ckddn9496.tistory.com/82)

- FileAppender 상속하여 로그 파일을 rollover 진행
  - `rollover`: 타깃 파일 바꾸는 것으로 이해하면 돼!! 
- 즉! RollingFileAppender가 타깃 파일로 log.txt에 로그 메시지를 appender 하다가 어느 지정한 조건에 다다르면, 타깃 파일을 다른 파일로 바꿀 수 있다 ✔
