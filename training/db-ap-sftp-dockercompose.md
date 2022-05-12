## `DB SERVER` + `AP SERVER` + `SFTP SERVER` 도커 컴포즈로 띄우기
### 1. 아키텍처
- ![image](https://user-images.githubusercontent.com/61215550/167992939-05b59667-b251-4099-bc98-74968b8df32d.png)

### 2. `docker-compose-[서버명].yml` 각각 분리해서 준비
- 기본적으로 `Dockerfile` 이용해 도커 컴포즈 구성하지만 귀찮으니까 도커 컴포즈 파일만 구성함! 😁
- ![image](https://user-images.githubusercontent.com/61215550/167993070-40f31d48-c8b9-4dd2-a6dc-fcb3c54485b7.png)
- 실행 명령어 ✔
  - `docker-compose -f docker-compose-[db서버].yml f docker-compose-[ap서버].yml f docker-compose-[sftp서버].yml up -d`

#### 코드
- `docker-compose_mssql.yml`
```yml
version: "3.8"
services:
  mssql_db :
    image: mcr.microsoft.com/mssql/server:2017-latest
    container_name: mssql_db
    hostname: mssql_db ⭐
    ports:
      - "1433:1433"
    expose: 
      - "1433"
    volumes: ⭐ 데이터 영속성을 위해
      - volume-server:/var/opt/mssql/
    environment:
      ACCEPT_EULA: Y
      SA_PASSWORD: your@Password
    networks: ⭐ 네트워크 공유는 필수!
      - test-network


networks:
  test-network:
volumes: 
  volume-server:
```
- `docker-compose_server.yml`


```yml
version: "3.8"
services:
  spring-server:
    image: openjdk:8-jre
    ports:
      - "8888:8181"
    container_name: spring_server
    volumes: ⭐ 로컬 경로:컨테이너 내부 경로 >> 데이터 변경시 동일시하게 동작된다!
      - ../build/libs:/app
      - d:\sftp\admin:/file
    entrypoint: ["java", "-jar", "/app/spring-docker-0.0.1-SNAPSHOT.jar"]
    depends_on:
      - mssql_db
    links:
      - mssql_db
      - sftp
    networks:
      - test-network


networks:
  test-network:
```

- `docker-compose_sftp.yml`


```yml
version: "3.8"
services:
  sftp:
    container_name: sftp_server
    image: atmoz/sftp
    volumes: ⭐ 로컬 경로:컨테이너 내부 경로
      - d:\sftp\home\upload:/home/foo/upload
    ports:
      - "2222:22"
    command: foo:pass:1001
    networks:
      - test-network

networks:
  test-network:
```
### 3. 빌드 
- `bootJar`를 통해 생성
- ![image](https://user-images.githubusercontent.com/61215550/167993651-3a4dc038-9ece-43c2-a970-65c912214a55.png)

### 4. `sftp` 연결 및 동작 코드
- `SftpUtil.java`
```java
@Slf4j
public class SftpUtil {
    JSch jSch;
    Session session;
    Channel channel;
    ChannelSftp channelSftp;

    // jsch 객체 생성 및 연결
    public void connect(String host, String user, String password, int port) throws Exception {
        log.info("connecting ...." + host);
        jSch = new JSch();
        session = jSch.getSession(user, host, port);
        session.setConfig("StrictHostKeyChecking", "no");
        session.setPassword(password);
        session.connect();

        channel = session.openChannel("sftp");
        channel.connect();
        channelSftp = (ChannelSftp) channel;
    }

    // 접속 해제
    public void disconnect() {
        if(session.isConnected()){
            log.info("disconnecting...");
            channelSftp.disconnect();
            channel.disconnect();
            session.disconnect();
        }
    }

    // 파일 업로드
    public void upload(String fileName, String remoteDir) throws Exception{
        FileInputStream fis = null;

        connect("sftp","foo","pass", 22);
        try{
            // 입력 파일 가져오기
            File file = new File(fileName);
            fis = new FileInputStream(file);

            // 업로드하려는 위치에 디렉토리 변경
            channelSftp.cd(remoteDir);
            // 파일 업로드 진행
            channelSftp.put(fis, file.getName());

            fis.close();
            log.info("File uploaded successfully - " + file.getAbsolutePath());
        }catch (Exception e){
            e.printStackTrace();
        }
        disconnect();
    }
}
```

- `Main.java`
```java
    @GetMapping("/sftp")
    void sftp테스트() throws Exception {
        String localPath = "file/test.txt";

        // 파일 생성 시 >> 유저명/[업로드하고자 한 파일명]
        // 로컬 경로, 서버 경로
        /**
         * 여기서 서버 경로는 /home/[유저명] 이 기본 루트값 ⭐
         */
        sftpUtil.upload(localPath, "./upload"); ⭐ sftp 볼륨 설정시 루트 경로 
    }
```
