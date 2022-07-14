## ELK Stack + Kfaka
> [참고자료](https://pearlluck.tistory.com/583) <br>
> [참고자료](https://elastic-stack.readthedocs.io/en/latest/e2e_kafkapractices.html)


![image](https://user-images.githubusercontent.com/61215550/178900123-a36ce213-07da-4467-ade3-ce7688f90bf1.png)

### 1. 왜 사용하지?
- 로그를 따로 관리하지 않고 이렇게 파일에 쌓아두게 되면 아래와 같은 문제 발생 ㅠ,ㅠ
  - 로그레벨 파악 어려움
  - 검색어 분석 어려움
  - 날짜, 시간에 따라 로그 분석 어려움
  - 과거 로그로 인해 디스크 공간을 너무 차지 ㅠ,ㅠ

### 2. ELK
- ![image](https://user-images.githubusercontent.com/61215550/178898525-8c0d8687-4503-4ac7-af30-a8b8f3a63709.png)
- 로그 데이터 검색 및 분석하는 도구
 - ✔ 계속 쌓이는 웹로그 어떻게 __저장???__ 어떻게 **검색???** **분석???** 
#### 2.1 ElasticSearch - 데이터 검색 및 분석을 담당하는 엔진
- 분산형 검색엔진
  - Apache Lucene기반으로 구축되어 있어서 **분산형 및 개방형** 특징
  - JAVA로 개발
- 실시간 분석시스템 
  - 클러스터가  실행되고 있는 동안 계속해서 데이터 입력하고 그와 동시에 실시간에 가까운 속도로 검색 및 집계 수행
  - 역인덱스 데이터 구조 사용 >> 풀텍스트 검색 가능
- 데이터저장 역할
  - LogStash 통해 수신된 데이터를 저장소에 저장하는 역할
  - 데이터 중심부에 저장하여 예상되는 항목 검색 + 예상치 못한 항목 밝혀냄
  - 정형, 비정형, 위치정보, 매트릭 등 원하는 방법으로 다양한 유형의 검색 수행 및 결합 가능
  - 표준 Restful API + JSON 사용
#### 2.2 Logstash - 데이터 수집/변환 Elasticsearch 전송(데이터 수집 파이프라인)
- 데이터수집엔진
  - 오픈소스 서버측 데이터처리 파이프라인
  - JAVA Runtime 가상머신 위에서 돌아감
  - 출력API  ElasticSearch 지원 시작 >> Logstash(입력) --> ElasticSearch(출력) 보편화
#### 2.3 Kibana - Elasicsearch 에 저장된 데이터 시각화해주는 웹 인터페이스 
- 웹 프론트엔드 서비스
  - 데이터 검색하고, 시각화하는 오픈소스 프론트엔드 서비스
  - 시각화 담당 `HTML + JS` 엔진

#### 2.4 (추가) Beats
- 서버에 설치하는 에이전트
- 다양한 유형의 데이터 `ElasticSearch` `Logstash` 전송할 수 있는 오픈소스 데이터발송지
- ![image](https://user-images.githubusercontent.com/61215550/178899417-afc09a7f-1f36-4479-98d6-12b33a175450.png) 

### 3. 장점
- 강력한 유연성과 호환성
- 자유스키마
- 확장가능 데이터베이스
- 데이터처리절차 개별설정
- 사전에 준비된 시각화도구
- 실시간 데이터처리

### 4. 단점
- 초기데이터 구성 및 이관문제
- 커널변수의 불필요한 사용
- 시간대 일관성이 깨지는 사용

### 5. 비교 `Kafka` 
> [참고자료](https://mygumi.tistory.com/400)
#### 5.1 Kafka 도입 이유
- 트래픽 몰리면 `Logstash` `Elasticsearch` 만으로 부하 견디기 힘들어 ㅠ,ㅠ

#### 5.2 Kafka 개념 
- `Pub-Sub` 모델 가지는 분산 메시징 플랫폼
- 기존 메시징 시스템처럼 Broker가 Consumer 에게 직접 메시지 전송하는 방식 아님!!
- Consumer가 Broker로부터 직접 메시지 가져가는 방식
