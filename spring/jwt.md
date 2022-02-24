## JWT (Json Web Token)
> [참고 링크](https://shinsunyoung.tistory.com/110)

- 서버기반(세션) VS 토큰기반(JWT)
- (요청, 응답) + 토큰을 함께 보내 사용자 유효한지 확인

![image](https://user-images.githubusercontent.com/61215550/155456217-e594aa6c-d68c-4bed-ac18-7a6e25f6a275.png)

### 특징
- __무상태성__
  - 토큰 >> 클라이언트에 저장 >> 별도의 저장소 x
- __확장성__
  - 구글, 페이스북, 네이버 로그인 등
- __무결성__
  - `HMAC(Hash-based Message Authenticaton)` 발급 후 토큰 정보 변경 불가
- __보안성__
  - 클라이언트 > 서버 (요청) @@@@ 쿠키 전달 x >> 쿠키의 취약점 사라짐 


### JWT
- 토큰 기반 인증 시스템의 대표적인 구현체

![image](https://user-images.githubusercontent.com/61215550/155456506-02757df6-2e66-4ce1-98b3-510a902be261.png)
#### 헤더
- 토큰의 타입
- 알고리즘 지정하는 정보

```json
{
  "typ": "JWT",
  "alg": "HS256"
}
```
#### 정보
- `Claim`: 정보의 한 덩어리
  - 등록된 클레임
  - 공개 클레임
  - 비공개 클레임
- 토큰에 담을 정보
- 키, 값으로 구성

```json
{
    "iss": "ajufresh@gmail.com", // 등록된(registered) 클레임
    "iat": 1622370878, // 등록된(registered) 클레임
    "exp": 1622372678, // 등록된(registered) 클레임
    "https://shinsunyoung.com/jwt_claims/is_admin": true, // 공개(public) 클레임
    "email": "ajufresh@gmail.com", // 비공개(private) 클레임
    "hello": "안녕하세요!" // 비공개(private) 클레임
}
```

#### 서명
- 해당 토큰이 조작되었거나 변경되지 않았음을 확인하는 용도
- 헤더의 인코딩 값 + 정보의 인코딩 값 = 비밀키 사용해 해쉬값 생성 ✔

---
## 실습
> [프로젝트 링크](https://github.com/Java-Techie-jt/spring-security-jwt-example)

![image](https://user-images.githubusercontent.com/61215550/155466802-b31f2b36-4d48-49a1-950e-42cf5bde60a9.png)
![image](https://user-images.githubusercontent.com/61215550/155467338-cf61fd26-7e04-4e89-92a8-9f699bce9f3a.png)

