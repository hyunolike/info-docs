## mac m1 에서 oracle 사용방법 
> [참고자료](https://shanepark.tistory.com/400) <br>
> [oci-oracle-xe](https://github.com/gvenzl/oci-oracle-xe)

### 준비
- docker
- colima (Apple M 칩에서 실행가능하도록 환경 구성)
  - 실행 `colima start --memory 4 --arch x86_64`
  - 볼륨 파일 권한 설정 `sudo chown -R 54321:54321 [./colima/oracle-data] 이거는 폴더 위치` 
- oracle-oci-xe

### 과정
#### 1. 위 준비과정 끝났다는 전제하 > 도커컴포즈 파일 준비
```yml
version: '3'
services:
  oracle:
    image: gvenzl/oracle-xe
    container_name: oracle-oci
    volumes:
      - ./colima/oracle-data:/opt/oracle/oradata gvenzl/oracle-xe ✅ 해당 볼륨 파일 먼저 생성 후, 권한 지정한다 !!! 그 다음으로 도커 실행하면 되
    ports:
      - 1521:1521
    environment:
      - ORACLE_PASSWORD=1234 
```


- 여기서 환경변수는 위에 깃헙 자료에서 확인!
- <img width="225" alt="image" src="https://user-images.githubusercontent.com/61215550/201349544-563132cf-97ec-47c3-8260-aaad3d9f1659.png">
##### 결과
<img width="1455" alt="image" src="https://user-images.githubusercontent.com/61215550/201349618-f9006020-7df0-467b-9a95-eb5940fee9a3.png">

#### 2. 디비 연결 결과
- <img width="614" alt="image" src="https://user-images.githubusercontent.com/61215550/201349719-2dff0f12-0363-411a-a176-4f97c1d8d8f5.png">
- <img width="225" alt="image" src="https://user-images.githubusercontent.com/61215550/201350037-05fbd916-7828-4ba4-a7be-3a35f0fc3b17.png">
