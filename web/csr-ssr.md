## CSR + SSR 구축
> [참고자료](https://tecoble.techcourse.co.kr/post/2021-09-10-ssr/)
### 1. 구조
> ✔ `reverse proxy`
![image](https://user-images.githubusercontent.com/61215550/178672047-1aa99bc6-685b-459a-895c-155b6cd2b21f.png)

### 2. 도입 계기
1. 프론트엔드 개발자가 서버 쪽 코드도 개발할 수 있어 자유도가 높아짐
2. SEO(검색 엔진 최적화) 향상
3. 페이지 초기 렌더링이 CSR보다 빨라짐

### 3. 로그인 로직
|로그아웃 상태에서 로그인|로그인 상태에서 웹페이지 진입|
|-----------------------|-----------------------------|
|![image](https://user-images.githubusercontent.com/61215550/178673183-bc3b97fb-77eb-4802-b700-f6f1402e7de8.png)|![image](https://user-images.githubusercontent.com/61215550/178673218-ac2ec0b8-e990-4700-9e9f-ea0d9ab0ef0a.png)|

