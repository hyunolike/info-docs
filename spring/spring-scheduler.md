## Spring Sheduler
> [참고자료](https://dev-coco.tistory.com/176)

### @Scheduled
- 일정한 시간 간격으로, 혹은 특정 시간에 코드 실행되도록 설정
#### 사용 방법
1. `@EnableScheduling` 추가
2. 스케줄링 작업할 클래스 생성
  - 😛 핵심!! >> `@Component(@Service 등)` 즉, 스프링 빈 등록한 클래스!
  - @Scheduled 규칙 >> Method는 void 타입 / 매개변수 사용 불가
### 속성
#### `fixedDelay`
- `milliseconds` 단위
- 이전 Task 의 종료 시점으로부터 정의된 시간만큼 지난 후 Task 실행

#### `fixedDelayString`
- 위에꺼라 같음 >> 단지 `문자열`로 값을 표현하겠다는 의미

#### `fixedRate`
- milliseconds` 단위
- 이전 Task의 시작 시점으로부터 정의된 시간만큼 지난 후 Task 실행

#### `fixedRateString`
- 이것도 같아

#### 🎉 `cron`
- 작업 예약
- <img width="723" alt="image" src="https://user-images.githubusercontent.com/61215550/224703517-92950bae-f909-46e5-a02f-0f9d75a38992.png">
