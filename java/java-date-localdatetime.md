## `Java` 날짜 비교
- `Java 8` 이후
  - LocalDate
  - LocalDateTime
- `Java 8` 이전
  - `Date`
  - `Calendar`

### 1. LocalDate
- `public boolean isAfter(ChronoLocalDate other)`
  - 주어진 날짜가, 파라미터로 전달받은 날짜보다 클 경우 `true` 리턴
- `public boolean isBefore(ChronoLocalDate other)`
  - ... 작을 경우 `true` 리턴
- `public boolean isEqual(ChronoLocalDate other)`
  - ... 같을 경우 `true` 리턴
- `public int compareTo(ChronoLocalDate other)`
  - 주어진 날짜가
  - 파라미터로 전달받은 날짜와 같은 경우 `0`
  - ... 클 경우 `양수`
  - ... 작을 경우 `음수`
  - 힛! 리턴하기

