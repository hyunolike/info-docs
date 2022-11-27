## SDK vs REST API
> [참고자료](https://velog.io/@hacha2011/SDK%EC%99%80-API%EA%B0%80-%EB%AD%90%EA%B0%80-%EB%8B%AC%EB%9D%BC)

### REST API
- Representational State Transfer API
- HTTP URI로 리소스 표현 / 리소스에 대한 행위 HTTP Method 로 정의하는 방식
- API 목적 쉽게 파악 가능
- ✅ `request`
    - operation(POST,GET ...)
    - parameters(선택적)
    - endpotion (/example) URL
- ✅ `response`
    - json, xml과 같은 데이터 객체로 추출 


### SDK
- Software Deveopment Kit
- 실제로 api 호출해주는 메소드 포함
- response 또한 json같은 형태일 필요 없음 >> analyze response object로 받을 수 있음 

### 차이!!! 🎉
- API: 결과 받아오기 위해 어떤 작업을 수행해야 하는지 알려줄 뿐 이후의 처리는 개발자 몫
- SDK: 소프트웨어 개발을 위한 실제 코드까지 있음
- 😛 SDK가 좀더 크고 편한 도구!!!
