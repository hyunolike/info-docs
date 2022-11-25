## `jsp` `thymeleaf` 차이점
> [참고자료](https://velog.io/@come_true/Thymeleaf-vs-JSP)

### 1. `jar` export 가능 여부
- spring 프로젝트 빌드 >> 기본적으로 `jar`
  - ✔ `war` 는 웹서버 / WAS 필요! (사전에 정의된 구조만 사용)
  - ⭐ 따라서 스프링 프로젝트에서는 jar로 export 되는 것이 편리
- 😛 `jsp`는 jar 패키징 불가 ㅠ,ㅠ / war 만 가능~~
- 😛 `thymeleaf` >> `jar` 패키징 & WAS 없어도 브라우저 띄울 수 있음!

### 2. 순수 HTML
- `thymeleaf` >> 순수 html 유지
- `jsp` >> 순수 html 유지 x / jsp + html 소스 뒤죽박죽~
  - ✔ jsp는 오직 서버를 통해서만 렌더링 가능 / html 응답결과 받아야만 화면 확인 가능!

### 3. Servlet
- `thymeleaf`: html 얻어오기 > 파싱 > 정해진 위치에 데이터 치환 > 웹페이지 생성
  - 📌 서블릿 변환되지 않기에 비즈니스 로직과 완전 분리
- `jsp`: 서블릿 변환 > 웹애플리케이션 서버에서 동작 > 필요한 기능 수행 및 생성 데이터 웹페이지와 함께 클라이언트 응답
  - 자바코드 사용 가능 / view + 비즈니스 로직 포함되 복잡하고 무거워져 ㅠ,ㅠ

### 4. 성능
- ![image](https://user-images.githubusercontent.com/61215550/203923089-d72e7184-6604-4d31-9d44-492b3a76617b.png)
- `jsp` > `thymeleaf` 응답 속도는 jsp가 더 좋음!

### (추가) was?
- 어차피 매번 재가동 하자나..ㅋ

