## BFF (Backend - For - Frontend) 
> [참고자료](https://tech.kakaopay.com/post/bff_webflux_coroutine/)
- ⭐ MSA 환경에서 최적의 방법으로 가져오기 위해 `비동기 방식` API 개발 및 데이터 효율적으로 전달하기 위해 BFF 패턴 적용

### 💡 BFF란
- 프론트엔드에 표현될 데이터를 위한 백엔드
  - 프론트엔드 데이터에 대한 책임을 백엔드가 가짐!
#### 프론트엔드 친화적인 API 서버 
![image](https://user-images.githubusercontent.com/61215550/229412322-c9ec8292-533e-45da-ba1c-9fde3f92e39b.png)

#### ⭐ API 조합기 역할
- BFF >> MSA 환경에서 다양한 서비스들의 데이터 조합 >> 프론트엔드 내려주는 API 조합기 역할 수행해야됨!



|기존|BFF|
|---|---|
|![image](https://user-images.githubusercontent.com/61215550/229412464-aa068eeb-fa8f-43ee-9a8d-0ae23a4cd027.png)|![image](https://user-images.githubusercontent.com/61215550/229412480-c36f2b48-3163-42bc-8746-d0bab8bbf54f.png)|

### 💡 다양한 환경(웹, 앱) 구동된다면 `GraphQL` 고려
- 모바일과 데스크톱으로 서비스 화면이 여러 개로 나눠져 있다면 BFF + GraphQL 검토!
#### `GraphQL`
- `프론트엔드` 에서 질의를 통해 자신에게 필요한 데이터를 백엔드로부터 질의해오는 기술
- ![image](https://user-images.githubusercontent.com/61215550/229412692-f21aab46-2176-42d7-86e0-a5fbee6d753e.png)
