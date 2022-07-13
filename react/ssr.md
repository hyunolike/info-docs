## SSR `server-side rendering`
> [참고 자료](https://d2.naver.com/helloworld/7804182)

### 1. SSR?
> 📌 SSR이 CSR에 비해 성능이 우수한 면도 있지만 모든 면에서 SSR이 CSR보다 우수하지는 않다.
- 서버에서 사용자에게 보여줄 페이지를 모두 구성하여 사용자에게 페이지를 보여주는 방식
- `jsp/servlet` 아키텍처 방식 사용
- 모든 데이터가 매핑된 서비스 페이지 >> 클라이언트 바로 보여줌
- 서버 사용하기에 클라이언트에서 구성하는 CSR에 비해 속도 느리지만 / 사용자에게 보여주는 콘텐츠 구성이 완료되는 시점은 빨라진다는 장점!! ✔
- `SEO(search engine optimizaqtion)` 쉽게 구성 가능
- ![image](https://user-images.githubusercontent.com/61215550/178626214-07c1e28a-0b2a-40ed-909d-66e511c97468.png)
#### 1.1 CSR
- SSR보다 초기 전송되는 페이지의 속도 빠름 
- 서비스에 필요한 데이터를 클라이언트(브라우저)에서 추가로 요청하여 재구성 >> 전체적인 페이지 완료 시점 SSR보다 느려짐 ㅠ,ㅠ
- ![image](https://user-images.githubusercontent.com/61215550/178626585-7c500bd8-0c4e-40ff-9690-26b443ecefae.png)

### 2. 개발 구조
![image](https://user-images.githubusercontent.com/61215550/178626741-3a0f6f57-c80d-40df-98a0-a6b050b22fd6.png)

### 3. Node.js 기반의 SSR 도입 이유
#### 3.1 Node.js 기반의 SSR은 universal language 인 JavaScript 최대한 사용 가능
#### 3.2 SSR 사용시 프런트엔드 영역과 백엔드 영역을 완전히 분리함으로써 생산성 높일 수 있음
- 페이지 소유권 온전히 프런트엔드에 존재하게 됨 ✔
- ![image](https://user-images.githubusercontent.com/61215550/178627057-2a231c4e-9442-4d29-a92b-6082f61f5010.png)
#### 3.3 SSR 아키텍처 구성시 다른 여러 가지 대안을 활용할 수 있는 토대

### 3. 롤백 플랜 ✔
> [참고자료](https://d2.naver.com/helloworld/2177909)
1. 사용자 부하를 받지 못하거나 장애가 발생하는 경우 CSR 페이지 노출
2. CSR 페이지가 장애가 발생한 경우 프런트엔드 전환 전 페이지 노출
- ![image](https://user-images.githubusercontent.com/61215550/178627999-df8bd6e7-d065-40fa-88bc-dd903ac3e863.png)
