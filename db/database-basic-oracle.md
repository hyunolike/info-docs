## 데이터베이스 개념 - 오라클
> [참고자료](https://www.youtube.com/watch?v=uEevQEsxjrs)
### 1. 데이터베이스 개념 이해
- 유용한 데이터 집합
- 데이터베이스 저장된 정보 >> 검색, 수정, 삭제 용이
#### 1-1. 파일시스템 문제점
- 데이터 종속 
- 데이터 중복
  - 일관성, 보안성, 경제성, 무결성
#### 1-2. 데이터베이스 정의
- 통합된 데이터
- 저장된 데이터
- 운영 데이터
- 공용 데이터
#### 1-3. 데이터베이스 특징
- 실시간 접근성
- 지속적인 변화
- 동시 공유
- 내용에 대한 참조

## ⭐ 오라클 데이터베이스의 저장 구조 
### 1. 데이터처리 🙄
- ✔ `Oracle`: 오라클 인스턴스 + 데이터베이스



|기존|개선|
|----|---|
|![image](https://user-images.githubusercontent.com/61215550/204711030-f4403c68-8406-4923-800d-7300fe16fbd2.png)|![image](https://user-images.githubusercontent.com/61215550/204711133-cc7865c7-d1f7-4505-b169-5ebd47fbd96a.png)|

### 2. 오라클 구조
- ![image](https://user-images.githubusercontent.com/61215550/204711522-be149781-9fa7-41fb-a737-2e101e7b90a9.png)
- ![image](https://user-images.githubusercontent.com/61215550/204711630-90103100-694e-4033-85b4-485113dbae29.png)
#### 2-1. 시스템 글로벌 영역 `SGA` 
- 오라클 데이터베이스 >> 모든 사용자의 제어 정보 + 데이터 포함!
- 사용자 실행하는 sql 문에 의해 검색 또는 변경되는 테이블 데이터를 저장하는 오라클 서버의 공유 메모리 영역
#### 2-2. SGA 영역의 구조
- ![image](https://user-images.githubusercontent.com/61215550/204711979-da0f3814-bffb-4f8d-b1fa-d9ce752f04ca.png)
### 3. 오라클 구조 정리 😛
> 3가지
#### 3-1 프로세스 
- ![image](https://user-images.githubusercontent.com/61215550/204712817-6a72e6dd-fe6c-4d2e-a3eb-37b0f0d6070f.png)
- 메모리에 상주해 있는 실행중인 프로그램
- 종류
  - 사용자 프로세스
  - 오라클 프로세스 - 서버 프로세스 & 백그라운드 프로세스
#### 3-2 메모리
#### 3-3 파일
