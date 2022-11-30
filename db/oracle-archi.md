## 오라클 논리/물리 적 구조 이해
> [참고자료](https://dataonair.or.kr/db-tech-reference/d-guide/dbms-1/?mod=document&uid=101841)
- ⭐ 데이터베이스 >> 논리적 구조 & 물리적 구조 나눠서 구성!
  - 데이터베이스 = 논리적 개념
  - 데이터 = 집합
- ⭐ 오라클은 여러 개의 테이블 스페이스라는 논리적 구조가 모여 **하나의 데이터베이스** 구성
- ![image](https://user-images.githubusercontent.com/61215550/204705850-b685160c-5d4d-4ced-936f-7115d3b02607.png)
### 1. 논리적 저장 구조
- `Tablespace` `Segment` `Extent` `Data Block` 4가지 ✔
#### 1-1. Tablespace 
- ![image](https://user-images.githubusercontent.com/61215550/204706263-275305ca-5bbb-40dc-b8d4-82648a7081d0.png)
#### 1-2. segment
- 테이블 ✔
- 테이블이 바로!! `Segment`
- ![image](https://user-images.githubusercontent.com/61215550/204708550-7ac2ad56-13f4-4852-ad85-d692d26364d1.png)
#### 1-3. Extent
- 하나 이상의 연속된 데이터 블록의 모임
- 세그먼트에 대한 공간 할당 단위
- 테이블 스페이스는 여러 개의 물리적 파일 / Extent는 반드시 하나의 데이터 파일에만 존재 가능 ⭐
- ![image](https://user-images.githubusercontent.com/61215550/204708700-5b8400ef-7669-4c23-aea4-ed8cff6def50.png)
#### 1-4. Block
- `I/O` 단위로서 모든 데이터 Block으로 이뤄짐!
- ✔ DB에서 데이터 검색 시 >> 아주 작은 데이터 하나만을 찾으려고 할 때도 최소한 하나의 Block 에 저장된 전체 데이터에 대해서는 스캔이 이뤄진다는 뜻
- ![image](https://user-images.githubusercontent.com/61215550/204708826-38055f6f-6572-480f-a566-9314eb4c97f0.png)

### 2. 물리적 저장 구조 
> [참고자료](https://zeroco.tistory.com/23)
- `데이터 파일` `컨트롤 파일` `redo 로그 파일` `설정 파일` `alert/trace 로그 파일` `백업 파일`
#### 2-1. 데이터 파일
- 오라클에서 관리하는 데이터 >> 실제로 저장되는 디스크 상의 파일
- ![image](https://user-images.githubusercontent.com/61215550/204709581-a01e865b-1239-4d5a-9316-a50f47746645.png)
#### 2-2. 컨트롤 파일
- 데이터베이스의 물리적 구조, 이름, redo 로그파일들의 위치정보, 생성 시간, 현재 로그 번호, 체크포인트 정보 등 저장된 파일
#### 2-3. Redo 로그파일
- 데이터베이스 변경 내역 저장하는 파일
#### 2-4. 설정 파일
- 데이터베이스와 데이터베이스 서버와 관련된 설정 정보 등 저장
#### 2-5. alert / trace 로그 파일
- 오라클 서버 내부에서 오류 발생 경우, 그 오류에 대한 정보나 메시지 저장하는 파일
