## docker 컨테이너 데이터 저장(`volume` `bind mount`) 
> [참고 자료](https://www.daleseo.com/docker-volumes-bind-mounts/)

![image](https://user-images.githubusercontent.com/61215550/167335189-7472bae0-ff88-4b48-8ffe-07913cc7b36b.png)
![image](https://user-images.githubusercontent.com/61215550/167335368-d11dc4e1-44a4-48bb-9d80-cb842ab52f71.png)

- 도커 컨테이너에 쓰여진 데이터는 기본적으로 컨테이너 삭제될때 함께 사라짐
- 하지만, 컨테이너 생명주기와 상관없이 데이터를 영속적으로 저장해야됨
- 뿐만 아니라, 여러개의 도커 컨테이너가 하나의 저장 공간을 공유해서 데이터 읽거나 쓰여야함

### 볼륨 Volume
- 도커 컨테이너에서 생산되고 사용되는 데이터를 영구적으로 저장하기 위한 방법
- 바인드 마운트가 디렉토리 구조나 os에 의존적인 반면, 볼륨은 도커에 의해 완전히 관리

### 바인드 마운트
- 호스트 파일 시스템의 특정 경로를 컨테이너로 바로 마운트 가능
- 호스트 머신의 파일과 디렉터리가 컨테이너에 마운트
  - 호스트 머신의 절대 경로로 참조 

#### 실습
- 로컬에 저장된 test.txt 파일 ✔
  - ![image](https://user-images.githubusercontent.com/61215550/167334286-acbc01c4-aaaa-4e39-917f-480fbe5afc80.png)
- 도커 컨테이너 실행 시 특정 경로로 마운트 설정! ✔
  - ![image](https://user-images.githubusercontent.com/61215550/167334335-64d3690f-f0e7-484a-bee3-b254df8213d3.png)
- 아래와 같이 도커 컨테이너에도 해당 파일이 영속 ⭐
  - ![image](https://user-images.githubusercontent.com/61215550/167334387-96545b71-8d8c-4697-9e14-18cd2eee9238.png)
- 반대로 도커내 컨테이너에서 해당 파일 생성하면 로컬쪽에도 생성되게 된다! ⭐
  - ![image](https://user-images.githubusercontent.com/61215550/167334510-4d3632ff-5f28-4536-8fb0-951b4578ffa8.png)
  - ![image](https://user-images.githubusercontent.com/61215550/167334521-1fc87492-280e-462d-92a0-364ee5fe04e8.png)
- `docker inspect`
  - ![image](https://user-images.githubusercontent.com/61215550/167334675-bf43134b-462a-464f-9f8e-45783af2f6de.png)

### 볼륨 vs 바인드 마운트
- ✔ Docker가 해당 마운트 포인트를 관리해주느냐 안해주느냐 차이!
