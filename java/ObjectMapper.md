## `ObjectMapper`
- `JSON` 형식 사용 >> 응답(직렬화), 요청(역직렬화)
- 직렬화
  - 데이터 전송 및 저장 >> 바이트 문자열이어야 하기 때문에 객체들 문자열 바꿔주는 것
  - `Object -> String`
- 역직렬화
  - 데이터 전송 후, 수신측에서 다시 문자열을 기존 객체로 회복시켜주는 것
  - `String -> Object`
  - 스프링 부트의 경우 기본적으로 `Jackson 라이브러리` 존재 >> `Object <-> JSON` 간 변환은 자동으로 처리

