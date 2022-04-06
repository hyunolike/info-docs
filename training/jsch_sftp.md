## `JSch` 라이브러리 사용해 sftp 서버단과 파일 주고 받기
- 로컬 피시로 테스트 하기 위해서는 `freeFTPd` 프로그램을 설치
- 추가적으로 자바에서는 sftp 통신을 하기 위해서는 `JSch` 라이브러리를 사용해야 된다.
### 개발 과정
#### 1. `freeFTPd` 프로그램 유저 생성
- 유저 생성시 기본적으로 홈 디렉터리는 원하는 경로로 설정한다. ⭐
  - `D:\`
#### 2. 자바 코드 작성
`SftpClient.java`

```java
public class SftpClient {
    // 접속할 ip, port, username, password
    String sftpIp = "0.0.0.0";
    int sftpPort = 22;
    String sftpUsername = "hyunho";
    String sftpPassword = "hyunho";

    // 보낼 파일 경
    String localPath = "D:/sftp/local-server/test1.sam";

    // 접속하려는 곳에서 파일 받을 경로
    String remotePath = "/sftp/remote-server/";



    public void sftpUploadTest() throws Exception
    {
        // JSch 객체 생성
        JSch jsch = new JSch();

        // 세션 객체 생성
        // 접속할 ip, port, username, password 설정
        Session session;
        session = jsch.getSession(sftpUsername, sftpIp, sftpPort);
        session.setPassword(sftpPassword);

        // ssh_config에 호스트 key없이 접속 가능하도록 property 설정
        Properties config = new Properties();
        config.put("StrictHostKeyChecking", "no");
        session.setConfig(config);

        // 접속
        session.connect();


        ChannelSftp channelSftp = null;
        Channel channel = null;

        try
        {
            // sftp 채널 오픈 & 연결
            channel = session.openChannel("sftp");
            channel.connect();

            channelSftp = (ChannelSftp) channel;
            channelSftp.put(localPath, remotePath);
        }
        catch(Exception e)
        {
            // 예외 처리
            //

        }
        finally
        {
            // 완료 후 접속 종료
            channelSftp.disconnect();
            channel.disconnect();
            session.disconnect();
        }
    }
}

```

`SftpTest.class`

```java
public class SftpTest {
    public static void main(String[] args) throws Exception {
        SftpClient sftpClient = new SftpClient();
        sftpClient.sftpUploadTest();
    }
}
```

#### 3. 결과
- 미리 설정된 로컬, 원격 정보에 따라 파일이 업로드 및 다운로드가 
