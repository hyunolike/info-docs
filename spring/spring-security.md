## 스프링 시큐리티
> [참고 자료](https://kdg-is.tistory.com/267)
- 어플리케이션의 보안(인증 + 권한) 담당하는 프레임워크
  - 사용하지 않으면 자체적으로 세션을 사용하여 체크 및 기타 다른 방법으로 체크

### 동작 위치
- `톰캣`
  - 다양한 필터 + 서블릿으로 구성
  - 보통 웹 개발하면 `Dispatcher Servlet` 하위에서부터 많이 다룸
  - Spring Security는 __필터 부분__ 조작✔
  - ![image](https://user-images.githubusercontent.com/61215550/169929099-453d4744-7214-4cdb-8079-eaac1e6214e0.png)
- `스프링 시큐리티`
  - 여러가지 필터로 구성 
  - 필터 순서대로 동작 >> `Filter Chain`
  - ![image](https://user-images.githubusercontent.com/61215550/169929137-4265f122-647d-423b-997e-34cd37f1e69c.png)

### 인증 + 인가
- 인증 성공 후 >> 인가 진행 
  - 인증: 해당 사용자가 본인이 맞는지 확인하는 절차
  - 인가: 인증된 사용자가 어떠한 경로에 접근이 가능한지 확인하는 절차
- 스프링 시큐리티의 인증 인가 방식 >> `Principal` == 아이디 / `Credential` == 비밀번호 >> 사용하는 `Credential` 기반의 인증 방식!!! ⭐
  - `Principal`(접근 주체): 보호받는 리소스에 접근하는 대상
  - `Credential`(비밀번호): 리소스에 접근하는 대상의 비밀번호
