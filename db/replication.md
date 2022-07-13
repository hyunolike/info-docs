## 1. Replication
> [참고자료](https://nesoy.github.io/articles/2018-02/Database-Replication)
- 영어 뜻 >> 원작의 모방
- 두 개 이상의 DBMS 시스템을 `Master / Slave` 로 나눠서 동일한 데이터 저장 방식
- ![image](https://user-images.githubusercontent.com/61215550/178668787-ea213b18-a9b7-4c3e-b372-0145c186381e.png)

### 장점
- Query 대부분은 `Select` 차지
- 부하 낮추기 위해 많은 `Slave Database` 생성 시 >> `Read(Select)` 성능 향상 효과 얻음
- `Master Database` 영향없이 로그 분석 가능

## 2. Clustering
- 여러 개의 DB를 수평적인 구조로 구축하는 방식
- ![image](https://user-images.githubusercontent.com/61215550/178670142-0c84a65b-77f7-4fe3-9ad1-837343519bb7.png)

### 장점
- 노드들 간의 데이터 동기화하여 항상 일관성있는 데이터 얻을 수 있음
- 1개의 노드가 죽어도 다른 노드가 살아 있어 시스템을 계속 장애없이 운영 가능

### 단점
- 여러 노드들 간의 데이터를 동기화하는 시간이 필요 >> `Replication` 비해 쓰기 성능 떨어짐
- 장애 전파된 경우 처리 까다로우며, 데이터 동기화에 의해 스케일링에 한계 존재
