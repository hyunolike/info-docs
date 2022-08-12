## Json 명명 규칙 선택 `snake_case` `camelCase`
> [참고자료](https://stackoverflow.com/questions/5543490/json-naming-convention-snake-case-camelcase-or-pascalcase)

- Twitter & Facebook API: snake_case
  - Ruby, PHP 사용   
- Microsoft & Google API: camelCase
  - .NET, Java 사용
- ⭐️ 프로그래밍 언어의 규칙 관한 것????
### 스택오버플로우 답변
- json 규칙은 프로그래밍 언어와 독립적이여야 함!!! >> 만약, 파이썬 자바 2가지 로 개발했다고 json 명명 규칙이 바뀌는게 이상해
- 대부분의 클라이언트는 웹앱 >> `camelCase` 선호
- <img width="695" alt="image" src="https://user-images.githubusercontent.com/61215550/184266188-33612077-97c0-4a27-988b-9ac988f9b609.png">
- 🙂아래의 자동 생성?? 언어별 json 해석하고 생성하는 거에 따라 선택해도되
- <img width="749" alt="image" src="https://user-images.githubusercontent.com/61215550/184266306-3c066ffa-fdf1-4898-900c-18ce46e239d6.png">


### 구글 JSON 스타일 가이드
> [사이트 바로가기](https://google.github.io/styleguide/jsoncstyleguide.xml?showone=Property_Name_Format#Property_Name_Format)

- 속성 이름은 의미가 정의된 의미 있는 이름
- 속성 이름 camelCase ASCII 문자열
- 첫 번째 문자는 문자, 밑줄(_), 달러 기호여야 함
- 예약어 사용 금지



