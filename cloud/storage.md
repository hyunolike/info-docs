## Storage 
> [참고자료](https://www.alibabacloud.com/ko/knowledge/difference-between-object-storage-file-storage-block-storage)

### 📌Data Storage
- 스토리지: 컴퓨터가 접근할 수 있는 데이터를 저장하기 위한 별도의 장소 또는 장치
- 최근, `비정형 데이터` 쉽게 저장하고 빠르게 검색할 수 있는 **스토리지 아키텍처** 중요해짐
- **오브젝트 스토리지** >> 주요 스토리지 중 하나로서 급부상

### ✔ Storage 수준별 분류
- 1차 스토리지: RAM과 같이 내부 장치로 쓰이는 스토리지
- 2차 스토리지: 하드디스크, 테이프 등과 같이 외부 장치로 쓰이는 스토리지
- 3차 스토리지: 클라우드 스토리지

### ✔ Storage 유형별 분류
- 블록, 파일, 오브젝트 스토리지 분류


|유형별 분류|설명|참고 자료|
|-----------|------|----------|
|`DAS(Direct Access Stroage)` - **Block Storage**|- 전용 케이블 이용해 서버와 스토리지 직접 연결하는 방식<br>- 일반 컴퓨터에 사용하는 외장하드 방식|![image](https://user-images.githubusercontent.com/61215550/182004913-09954d5f-57c3-4e22-aaae-4cf9d5bac4a6.png)|
|`NAS(Network Access Storage)` - **File Storage**|- 네트워크에 연결되어 사용 권한이 할당된 내부 사용자 및 외부 사용자들이 자유롭게 데이터를 검색, 저장할 수 있는 방식|![image](https://user-images.githubusercontent.com/61215550/182004926-e3b136ac-5dc7-49e5-9050-5f330662c290.png)|
|`SAN(Storage Area Network)` - **Block Storage**|- 여러 사용자가 동시에 엑세스 할 수 있으며 블록 스토리지|![image](https://user-images.githubusercontent.com/61215550/182004934-9eeed601-a625-4096-94b0-b674d282a346.png)|


### ✔ 데이터 저장방식에 따른 분류
- ![image](https://user-images.githubusercontent.com/61215550/182004940-e006ac0c-6163-4141-ab2b-28db7c3480ac.png)
- Blcok Storage
  - 데이터를 블록이라는 고정된 크기의 단위로 나누어 스토리지에 저장
  - 각 블록은 블록이 저장된 위치로 가리키는 고유의 주소를 가지고 있어 주소만 알고 있으면 분산 저장된 데이터를 찾아 하나의 데이터로 재구성
- File Storage
  - 데이터는 파일시스템이 디렉토리에 저장되며, 윈도우 탐색기와 같은 계층형 구조로 구성
  - 파일마다 파일의 위치, 크기, 생성일, 블록 위치 등에 대한 정보를 가지고 메타 데이터를 가지고 있어 파일을 검색하거나 수정할 시 OS 내 파일 시스템이 해당 작업을 지원
- Object Storage
  - 오브젝트라고 불리는 각각의 데이터 단위가 개별 단위로 저장되는 데이터 저장소 유형
  - PDF, 비디오, 오디오, 텍스트, 웹사이트 데이터나 기타 다른 파일 유형 등 사실상 **거의 모든 데이터 유형** 가능
  - 구조화되지 않은 데이터의 대량 저장을 위한 데이터 스토리지 아키텍처 / 각 데이터 조각을 하나의 객체로 개별 저장소에 보관하며 메타데이터와 고유 식별자를 함께 저장하므로 데이터 엑세스와 검색이 용이한 스토리지 저장방식
- ![image](https://user-images.githubusercontent.com/61215550/182005010-0fb3959a-3ee9-411e-964e-12e5c151285e.png)
