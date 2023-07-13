## CGI
> [참고자료](https://bentist.tistory.com/40)
### 🖐 역사
- 초창기 웹 > 정적 페이지 단순히 보여주는 것 목적
- 동적 콘텐츠 필요
    - `CGI` 등장
### 👩‍💻 CGI
> Common Gateway Interface
- 웹 서버 상에서 사용자 프로그램을 동작시키기 위한 기술 규격
- ⭐ python, java, php 등 프로그래밍 언어 > CGI 규격 준수 프로그램 개발 가능
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/1dee1fcc-72f5-4d6f-824c-44aa647563e3)
#### 문제점
- 요청 > 독립적인 프로세스 생성
    - 시스템 부하 ㅠ,ㅠ
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/2ef52995-71c7-4710-a200-e5123319c370)
#### 해결
##### 🚚 첫번째야
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/09793ad3-0a79-4e24-a426-2a5837be4cea)
- `버스(서버) > 한 명의 전문 가이드(인터프리터) > 개별 가이드 생성 X`
##### 🚚 두번째야 📌
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/8558073e-458f-4b9a-91f9-eaa0a3d9ffce)
- 애플리케이션 처리 프로세스 > 미리 `데몬` 가동! > 웹 서버의 요청 `데몬` 처리

#### WAS
- `데몬` 처리 방식 발전
- 애플리케이션 전용 데몬 > 웹 애플리케이션 서버 발전!!!
