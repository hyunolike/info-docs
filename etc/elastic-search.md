# Elastic Search(엘라스틱 서치)
> [참고자료](https://sudarlife.tistory.com/entry/Elasticsearch-%EA%B0%84%EB%8B%A8-%EA%B0%9C%EB%85%90-%EC%9E%A5%EB%8B%A8)
- ![image](https://user-images.githubusercontent.com/61215550/160118830-f2edd46c-7560-409c-965d-80564a010336.png)
- 똑같이 DB 뽑아서 쓰는데 왜 더 빠를까?
  - 데이터 구조자체가 다르다
  - ![image](https://user-images.githubusercontent.com/61215550/160117807-944af41f-9ac3-4852-b164-02258ca807b7.png)
  - 위에 처럼 한번에 가져오는 구조
- 왜 관계형 DB를 사용하는가??
  - 엘라스틱만을 가지고 서비스를 만들수 있지만 추천하지 않는다!! __(아래의 이유 때문에)__
  - 장점: 무료, 전문가들 버그 고침, 새로운 버전 릴리즈, ⭐방대한양(빅데이터) 분석 및 처리 가능
  - 단점: 기술의 진입장벽 ㅠ,ㅠ, 이슈가 났을때 대응하기 어렵다... , 도큐먼트 간의 조인할수 없다!, 트랜잭션(한번에 묶어서라는 말)을 제공하지 않는다
- 즉, 엘라스틱 서치는 말그대로 __서치__ 에 중점을 둔 엔진
## 개념 다시!
- `http 프로토콜`로 접근 가능
  - `REST API`를 통해 데이터 조작 지원
  - ![image](https://user-images.githubusercontent.com/61215550/160119004-d7fa06eb-bd8f-4070-bb05-a7f26906db43.png)
- __역색인__
  - ✔ 일반적인 색인의 목적: '문서의 위치' 에 대한 INDEX를 만들어 빠르게 그 문서 접근하고자 하는 거 >> __책의 목차__ ⭐
  - ✔ 역색인의 목적: __문서 내의 문자와 같은 내용물__ 맵핑 정보를 색인해 놓는 것 >> __책 가장 뒤의 단어 별 색인 페이지__ ⭐
  - ![image](https://user-images.githubusercontent.com/61215550/160119313-bf69eed6-b504-4dea-9fa5-e4e619ea335c.png)
- 장점
  - 오픈소스 검색엔진
  - 전문 검색
  - 통계 분석
  - Schemaless
  - RESTful API
  - Multi-tenancy
  - Document-Oriented
  - 역색인(Inverted Index)
  - 확장성
- 단점
  - 완전 실시간 x
  - Transaction Rollback 지원 x
  - 데이터의 업데이트 제공 x
### 일반적인 구조?
- 검색에 필요한 부분들 >> 모니터링 >> 또하나의 서비스!!(데이터 트래킹) >> 필요한 데이터만을 엘라스틱 서치에 주입하는 방식!
![image](https://user-images.githubusercontent.com/61215550/160118239-ad4e5c10-43f6-4c0c-a122-449e6e5a6a24.png)

### 데이터를 추출하여 자동으로 엘라스티 에 데이터를 넣는 부분 담당 `logstash`
![image](https://user-images.githubusercontent.com/61215550/160118439-6eb4a20b-19bc-46fa-94cd-a4fbf8ef3f1e.png)

### 실제 프로젝트 적용 구조 예시
![image](https://user-images.githubusercontent.com/61215550/160119813-50c035da-e6e7-4c15-ab06-be2e64676070.png)
