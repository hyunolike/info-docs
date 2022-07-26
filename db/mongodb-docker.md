## mongoDB + `Docker` 로 띄우자
> [참고자료](https://7942yongdae.tistory.com/131)
- `MongoDB`: NoSQL 데이터베이스 / JSON 형태의 데이터를 저장하는 도큐먼트지향 데이터베이스

### 순서
#### 1. Docker - MongoDB 다운로드
- `docker pull mongo`

#### 2. 컨테이너 생성 및 실행
```
docker run \
    --name mongodb \
    -d \
    -p 27017:27017 \
    -e MONGO_INITDB_ROOT_USERNAME=root \
    -e MONGO_INITDB_ROOT_PASSWORD=root \
    mongo

or

docker run --name mongodb -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=root -e MONGO_INITDB_ROOT_PASSWORD=root mongo
```


|용어|설명|
|----|-----|
|`--name`|만들어서 사용할 컨테이너 이름 정의|
|`-d`|컨테이너를 백그라운드에서 실행|
|`-p`|호스트와 컨테이너 간의 포트 연결|
|`--restart=always`|도커가 실행되는 경우 항상 컨테이너 실행|
|`-e`|기타 환경|
|`mongo`|사용할 이미지 이름|

### 3. 도커 컨테이너 접속 및 디비 접속
- `docker exec -it mongodb /bin/bash`
- `mongo -u root -p root`
