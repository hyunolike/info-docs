## Optional - 함수형 사고를 하자!
> [참고자료](https://www.daleseo.com/java8-optional-after/)

### null 관련 문제
- 런타임 `NPE` 예외 발생
- NPE 방어 위한 NULL 체크 로직으로 코드 가독성 및 유지 보수성 떨어짐!

### Optional
- null이 될 수 있는 객체
- 레퍼 클래스

### 효과
- NPE 방어 코드 작성 안해도됨
- NULL 체크 안해도됨

### Optional 객체 생성
#### Optional.ofNullable(value)
- null인지 아닌지 확신할 수 없는 객체 담고 있는 Option 객체 생성
- `Optional.empty()` + `Optional.ofNullable(value)`
