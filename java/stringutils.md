## StringUtils 
> [참고자료](https://velog.io/@mooh2jj/JAVA-StringUtils-%EC%82%AC%EC%9A%A9%EB%B2%95)
- `org.apache.commons.lang` 의존성 추가
  - spring framework 기본적으로 추가
- 기본적으로 `null-safe` 한 연산!
- 자바의 String 클래스 문자열 관련 기능 강화한 클래스

### 유용한 메서드
#### 1. `isEmpty()`
- null 체크 & 길이 0 체크
- 사용 조건
  - String 아닌 객체 NULL 검증
  - ObjectUtis 사용 시
#### 2. `hasText()` 
- 문자열 유효성 검증 유틸 메서드
  - NULL 인것
  - 길이 0 인것
  - 공백 인것
- 문자열 하나라도 포함 >> `false` 
#### ... 나머지는 알아서 봐ㅋㅋㅋㅋㅋ
