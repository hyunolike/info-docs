## Oracle RAC `Real Application Cluster`
### 1. 사전 지식
- `Database`: 데이터 저장하고 있는 창고의 역할
- `Instance`: 창고의 데이터를 가져와 작업하는 작업장
#### 1-1. Cluster
- 2개 이상의 독립된 서버들과 Disk를 하나로 연결하는 기법
- Cluster 구성된 서버들 중 어느 서버에 접속해도 동일한 Disk 엑세스! >> 하나의 서버 또는 하나의 Disk 연결하는 것처럼 인식
- `Oracle clusterware` >> 높은 처리량 & 고가용성 보장! ✔
### 2. RAC
> 여러 개의 `Instance`가 하나의 `Database` 엑세스 가능
- ⭐ Oracle RAC = N개의 Instance + 1개의 Databse
- 동일한 `Datafile` 공유 및 엑세스
- ![image](https://user-images.githubusercontent.com/61215550/204703280-773ca525-a0be-4701-a372-5dce225c20b0.png)
#### 2-1. Oracle RAC Network
- `Public IP`: 각 노드에 대한 고유한 IP / 서버 주소와 동일 >> 노드 관리 목적으로 사용
- `Service IP`: 노드 장애 발생시 신속하게 인식 >> 다른 노드로 재연결 시간 향상
- `SCAN(Single Client Access Name)`: Cluster 내 서버 수 관계없이 로드벨런싱 및 고가용성 고려 >> 3개의 IP 주소 권장
- `Private IP(Cluster Interconnect)`: Cluster Node 별 통신을 위한 IP 목적

### 3. 단일 `Instance` vs `Oracle RAC`
- ![image](https://user-images.githubusercontent.com/61215550/204704141-433501d5-1f24-4760-82ed-854d0d721c3f.png)
