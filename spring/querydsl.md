## QueryDSL
> [참고자료](https://tecoble.techcourse.co.kr/post/2021-08-08-basic-querydsl/)
- (기존) `JPQL` 문자열 오타 및 문법적인 오류는 런타임 시점에 에러 발생
  - 이유. `Query`를 String으로 처리하기 때문 

### QueryDSL
> ✔ 정적 타입 이 >> SQL 등의 쿼리를 생성해주는 프레임워크
- 문자가 아닌 코드로 쿼리 작성 / 컴파일 시점에 문법 오류 확인 가능
- 자동 완성 등 ide 도움 받을 수 있음
- 동적인 쿼리 작성 편리
- 쿼리 작성 시 제약 조건 등을 메서드 추출 통해 재사용

