## Git - `tag`
> [참고 자료](https://inpa.tistory.com/entry/GIT-%E2%9A%A1%EF%B8%8F-%ED%83%9C%EA%B7%B8-%EA%B8%B0%EB%8A%A5-%EB%B0%8F-%EC%82%AC%EC%9A%A9%EB%B2%95-tag)
- 커밋 참조하기 쉽도록 알기 쉬운 이름을 붙이는 것 
- ✔ 특정 커밋을 가리키는 링크
- 보통 릴리즈 브랜치 >> 주석 태그
- 로컬 >> 일반 태그
- ![image](https://user-images.githubusercontent.com/61215550/175456987-53542804-ab36-40e2-97cd-c1b1fa45d815.png)
- Git tag 종류 2가지
  - `Lightweight`
  - `Annotated`

### 1. `Lightweight`
- 특정 커밋 가르키는 역할(포인터 역할)
- 단순히 버전같은 태그 이름만을 남기는 태그
- 태그 객체가 아닌 태그한 객체를 그저 가리키기만 ✔

### 2. `Annotated`
- 만든 사람, 이메일, 날짜, 메시지 >> 객체로 따로 저장
- GPG(GNU Privacy Guard)로 서명 가능
- 따라서 __Lightweight__ 태그와는 달리 고유의 저장공간 생성
- 태그한 객체의 메타데이터와 SHA-1 포함 >> 그 자체의 메시지와 ID를 갖고있는 객체 ✔

## 소스트리에서의 깃 태그 ✔
- 원하는 커밋에 태그 설정!
- ![image](https://user-images.githubusercontent.com/61215550/175457945-7d9e89ba-cdb3-40a6-a9f6-05d67d31bd49.png)


