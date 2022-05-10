## docker volume 활용한 Data 관리
> [참고 자료](https://medium.com/dtevangelist/docker-%EA%B8%B0%EB%B3%B8-5-8-volume%EC%9D%84-%ED%99%9C%EC%9A%A9%ED%95%9C-data-%EA%B4%80%EB%A6%AC-9a9ac1db978c)
- ⭐ 윈도우에서 도커 볼륨 위치 `\\wsl$\docker-desktop-data\version-pack-data\community\docker\volumes`
- 크게 3가지 방법
  - `volume` ✔ 어떤거 사용할지 모르겠으면 이거 사용해
  - `bind mounts`
  - `tmpfs`
- ![image](https://user-images.githubusercontent.com/61215550/167578288-bba58eeb-8d81-4392-b478-ef2f369fef38.png)
- ⭐ 올바른 Moount 유형 선택 >> Data가 Docker Host내에서 어디에 존재하는지!

### 1. Data 저장을 위한 최선의 방법 `volume`
- 도커가 관리하는 Host File System의 일부에 Data 저장
- 도커가 생성하고 관리하는 방식 ✔
- bind mount와 유사하게 동작
- `docker volume prune` >> 사용하지 않는 volume 정리 가능

### 2. Host의 File System 원하는 곳에 저장 `bind mount`
- Data가 Host System의 어디에든지 저장될 수 있다.
- Docker 초기부터 사용할 수 있었던 방식 / volume에 비해 기능이 제한적

### 3. HostSystem의 Memory에 저장 `tmpfs mount` 
- Host System의 Memory에만 저장 / 절대로 Host의 File System에는 저장되지 않음!
- Docker Host 또는 Container 내의 디스크에서 Data가 유지되지 않음






