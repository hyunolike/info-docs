# `Spring Security` = 인증, 인가 / `JWT` = 토큰기반이며 세션의 단점 해결


- [참고 블로그](https://brunch.co.kr/@springboot/491)

### 1. `Spring Session`
### 2. `JWT & Spring Boot`
### 3. `JWT & Spring Security`
---

- HTTP = 비접속형 프로토콜 ⭐
- __서버__ > 클라이언트의 보통 이전 상태 기억하기 위한 여러 가지 방법 >> 그중 `JWT` 
## 1. `Spring Session`
![image](https://user-images.githubusercontent.com/61215550/155476779-500f27c8-999c-40cd-b5cc-d79bf6953056.png)

- `Spring Session`
- `Spring Session Clustering`

![image](https://user-images.githubusercontent.com/61215550/155477094-018b51bf-87d8-4aa5-b42a-53241a59849f.png)
- ✔ 세션정보 일치하지 않는 문제점 발생!

![image](https://user-images.githubusercontent.com/61215550/155477269-734ae211-0642-4be4-86f5-573370646634.png)

### 세션 저장소 단점
- 세션 저장소에 매번 조회 ㅠ,ㅠ
  - 사용자 리소스 조회 요청 >> 권한 검증해야 하기 때문!! `인증 / 인가` 

## 2. `JWT & Spring Boot`
- `JWT` 토큰의 2가지 조건
  1. 유효한 사용자인지(유효한 토큰인지) 검증(인증)
  2. 리소스에 대한 권한이 있는지 검증(인가)

![image](https://user-images.githubusercontent.com/61215550/155478394-60c142aa-4936-404c-a7b7-6b9c4208e93a.png)
![image](https://user-images.githubusercontent.com/61215550/155478476-085e95b8-a140-49dd-ba9f-535150c3db14.png)

### `JWT` 장단점
![image](https://user-images.githubusercontent.com/61215550/155478628-bb13567f-881b-448d-b81f-0d7f57f81b2c.png)

## 3. `JWT & Spring Security`
> [코드 바로가기](https://github.com/sieunkr/spring-jwt/tree/master/spring-security-jwt)
- `Spring Security` 사용위해 >> 반드시 `RDBMS` 저장소 구축 ❌
- `JWT 인증 필터` > `Spring Security Config` 추가

![image](https://user-images.githubusercontent.com/61215550/155479129-f1c6a28e-92ce-4a2f-82bd-15b9e4133800.png)
