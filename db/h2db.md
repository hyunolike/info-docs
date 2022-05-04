## `H2` Local(In-Memory) mode vs Server(TCP) mode
> [참고 자료](https://lob-dev.tistory.com/13) <br>
> [참고 자료](https://pamyferret.tistory.com/entry/H2-SpringBoot%EC%97%90-H2-DB-%EC%97%B0%EA%B2%B0%ED%95%98%EA%B8%B0)


### 1. `Embedded` 모드 ⭐따로 설치가 필요 없다?!
- ![image](https://user-images.githubusercontent.com/61215550/166613039-671b4755-bd7d-4ba4-9790-1bdfea0bf608.png)
- H2 DB를 시스템의 메인 메모리에서(JVM 위에서) 구동시키는 방식 app이 종료된다면 저장, 수정된 Data 손실(휘발)
- 기본적으로 영속적이지 않은 방식
  - ✔ 데이터에 대한 영속성을 제공하는 방법 존재

### 2. `Server` 모드
- ![image](https://user-images.githubusercontent.com/61215550/166613156-e87e3c72-ef75-462e-8f6a-92484bf4665e.png)
- 하나의 시스템에서 서버 모드를 사용하는 경우 
- 별도의 프로세스(JVM)을 통해 DB 동작시켜 데이터베이스를 영속적으로 사용하는 방법

---
## H2 방식 📌
### 인메모리 방식
> 애플리케이션의 라이브러리를 통해 구동되는 방식 >> H2 DB 설치되어 있지 않아도 사용 가능한 방법⭐ 
- 스프링부트 어플리케이션이 실행됐을 때 메모리 내에서 동작하고 스프링부트 어플리케이션 종료되면 그대로 데이터 사라진다.
- 어플리케이션이 종료되면 그대로 데이터 사라진다 ✔

### TCP 서버 방식
> 로컬에 설치되어있는 H2 DB를 서버 방식으로 연결해서 사용 >> 기존 로컬 DB사용하는 것이기 때문에 데이터가 사라지 않는다. 
- 인메모리와 다르게 스프링부트 어플리케이션이 종료되어도 데이터가 사라지지 않는 방식

### 파일 방식
- H2 DB 데이터 파일 있는 곳의 경로와 파일명 지정해서 사용

## H2 초기 스키마/데이터 생성 전략 📌
### 1. JPA 자동 생성
### 2. schema.sql / data.sql 사용
