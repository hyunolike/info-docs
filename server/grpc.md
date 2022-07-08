## gRPC (Google Remote Procedure Call)
> [참고 자료](https://medium.com/naver-cloud-platform/nbp-%EA%B8%B0%EC%88%A0-%EA%B2%BD%ED%97%98-%EC%8B%9C%EB%8C%80%EC%9D%98-%ED%9D%90%EB%A6%84-grpc-%EA%B9%8A%EA%B2%8C-%ED%8C%8C%EA%B3%A0%EB%93%A4%EA%B8%B0-1-39e97cb3460) <br>
> [참고 자료](https://medium.com/naver-cloud-platform/nbp-%EA%B8%B0%EC%88%A0-%EA%B2%BD%ED%97%98-%EC%8B%9C%EB%8C%80%EC%9D%98-%ED%9D%90%EB%A6%84-grpc-%EA%B9%8A%EA%B2%8C-%ED%8C%8C%EA%B3%A0%EB%93%A4%EA%B8%B0-2-b01d390a7190)

### 1. 등장 배경
#### `Server-Client Model`
- PC 개념 없던 시절 >> `Monolothic` 구조
- 개선 >> `Server-Client Model` >> 네트워크  중요해짐✔ 
  - `OSI 7 layer` `TCP/IP` 등 네트워크 계층 구조 정의 및 발전

#### `IPC` 
> 프로세스: 컴퓨터에서 연속적으로 실행되고 있는 컴퓨터 프로그램
- 프로세스 기본적으로 __상호독립적__
  - 메모리 공유 X 
- 프로세스간 정보 공유 필요할 때
  - IPC(Inter Process Communication): 별도 수단 이용해 프로세스 통신하는 방법론 


|IPC 기법 종류|설명|문제점|
|------------|---------------|-----------|
|`Socket`|![image](https://user-images.githubusercontent.com/61215550/177911558-5aeaacd0-2bc0-4d29-9839-80730fbb01f5.png)|- 일련의 통신 과정을 직접 구현하기에 통신 관련 장애를 처리하는 것은 개발자 몫|
|`RPC`<br>(Remote Procedure Call)|![image](https://user-images.githubusercontent.com/61215550/177913117-86606e02-a488-492b-94d7-a74548be76df.png)|구현의 어려움|
|`REST`|![image](https://user-images.githubusercontent.com/61215550/177913964-c97de3ea-d7ec-4d1f-a6d4-ac40a618ad68.png)|데이터 포맷의 직렬화|

### 2. `gRPC` google Remote Procedure Call >> 큰 특징 ` HTTP/2` `PB`
- 기존 RPC 기능 X / 메시지(JSON)의 Serialize 할수 있는 PB(Protocol Buffer) 만 제공
- 현재, PB기반 Serizlaizer + HTTP/2 --> RPC 프레임워크 ✔
  - `Proto File` 만 배포하면 환경과 프로그램 언어에 구애받지 않음!!! >> 서로간 데이터 통신 가능 ⭐
#### `HTTP/2`
- `HTTP/1.1`
  - 클라이언트 요청이 올때만 서버가 응답하는 구조 
  - 요청마다 `connection` 생성 >> cookie 등 많은 메타 정보들을 저장하는 무거운 header가 요청마다 중복 전달되어 비효율적이고 느린 속도
- `HTTP/2`
  - 1개의 `connection` 으로 동시에 여러 개의 메시지 주고 받음
  - header 압축 >> 중복 제거 >> 효율적!!
  - 필요 시 클라이언트 요청 없어도 서버가 리소스 전달 가능(요청의 최소화)
- ![image](https://user-images.githubusercontent.com/61215550/177914599-fd88d9f4-4fde-4b66-933d-45338d63cdd2.png)

#### `ProtoBuf`(프로토콜 버퍼)
- 구글 사에서 개발한 구조화된 데이터를 직렬화하는 기법

#### `Proto File`
- Message and Field
- Package
- Service
