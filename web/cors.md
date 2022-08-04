## CORS (Cross-Origin Resource Sharing)
> [참고자료](https://evan-moon.github.io/2020/05/21/about-cors/) <BR>
> [참고자료](https://velog.io/@kysung95/%EC%A7%A4%EB%A7%89%EA%B8%80-CORS-%EB%9E%80)
- ![image](https://user-images.githubusercontent.com/61215550/182781487-78a30a59-ff4c-46ac-9ca7-b63aad72f9a5.png)
- ⭐ 즉, 도메인이 다른 서버끼리 서로 요청 주고 받을 수 있게끔 해주는 것!!
- 한 출처에서 실행 중인 웹 어플리케이션 >> 다른 출처의 선택한 자원에 접근할 수 있는 권한을 부여하도록 브라우저에게 알려주는 체제
- 요청의 출처가 다르면 서버의 응답 걸러냄? - [참고자료](https://velog.io/@frankle97/CORS%EB%9E%80)
- 접근제어 3가지 시나리오
  - 단순요청
  - 사전요청
  - 인증요청
- 해결 방법
  - 프론트 프록시 서버 설정
  - 직접 헤더 설정
  - 스프링부트 설정

### 1. 출처 `Origin`
- 서버의 위치 `https://google.com`
- 출처 위치 확인 ✔
  - ![image](https://user-images.githubusercontent.com/61215550/182777130-a6d6d816-9484-46c4-bc54-b61cc4beae7b.png)

### 2. SOP (Same-Origin Policy)
- **같은 출처**에서만 리소스 공유 가능 규칙!

### 3. 왜 정책 ??
- 기본적으로 클라이언트 애플리케이션 >> 돔, 어떤 서버와의 통신, 리소스의 출처 >> 아무런 제재없이 열람 가능!
  - 탈취가 쉬워짐!!

### 4. 같은 출처, 다른 출처 구분
- `Scheme` `Host` `Port` 3가지 동일하면 됨!
- ![image](https://user-images.githubusercontent.com/61215550/182777581-1a1b1d9b-35f6-4388-8dd9-817c65984cc3.png)
- ![image](https://user-images.githubusercontent.com/61215550/182777619-fd2bf994-cfc7-4f4a-bee7-df0a31259105.png)


### 5. `CORS` 동작 방식 ⭐
#### 5.1 Preflight Request
- 예비 요청 >> 본 요청 보내기전 브라우저 스스로 요청을 보내는 것이 안전한지 확인하는 것
- ✔ CORS 정책 위반 여부 판단하는 시점 >> 예비 요청에 대한 응답 받은 이후!
- 📌 모든 요청마다 두 번씩 요청 보내는 것은 아님!
```http
OPTIONS https://evanmoon.tistory.com/rss

Accept: */*
Accept-Encoding: gzip, deflate, br
Accept-Language: en-US,en;q=0.9,ko;q=0.8,ja;q=0.7,la;q=0.6
Access-Control-Request-Headers: content-type
Access-Control-Request-Method: GET
Connection: keep-alive
Host: evanmoon.tistory.com
Origin: https://evan-moon.github.io ⭐ 출처!
Referer: https://evan-moon.github.io/2020/05/21/about-cors/
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: cross-site
```

#### 5.2 Simple Request
- ...
