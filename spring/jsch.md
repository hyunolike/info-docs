## `Jsch`
> [공식 문서](http://www.jcraft.com/jsch/)
- 오픈소스 ✔
- `shtp` `ssh` 사용해 원격 서버 접속할 수 있는 유용한 api 제공 ✔
- `sftp` 프로토콜 방식을 좀더 쉽게 연결하여 전송 가능
- 전송 간의 상태 등을 callback 통해 받을 수 있다

```xml
<dependency>
    <groupId>com.jcraft</groupId>
    <artifactId>jsch</artifactId>
    <version>0.1.55</version>
</dependency>
```

### 예제
```java
  String username = "root";
  String host = "192.168.56.1";
  int port = 22;
  Stirng password = "root";
  
  System.out.println("Connecing to" + host);
  
  // 2. 세션 객체 생성
  try{
    // 1. jsch 객체 생성
    JSch jsch = new JSch();
    session = jsch.getSession(username, host, port);
    // 3. 패스워드 생성
    session.setPassword(password);
    // 4. 세션과 관련된 정보를 설정
    java.util.Properties config = new java.util.Properties();
    // 4-1. 호스트 정보 검사하지 않음
    config.put("StrictHostKeyChecking", "no");
    session.setConfig(config);
    
    // 5. 접속
    session.connect();
    
    // 6. sftp 채널 열기
    channel = session.openChannel("exec");
    
    // 7. 채널을 ssh용 채널 객체로 캐스팅
    ChannelExec channelExec - (ChannelExec) channel;
    
    System.out.println("Connect to" + host);
    
    channelExec.setCommand("touch /test/jschTest.txt");
    channelExec.connect();
    
    System.out.println("Connect to" + host);   
  }catch(JSchException e){
    e.printStackTrace();
  }finally{
    if(channel != null){
      channel.disconnect();
    }
    if(session != null){
      session.disconnect();
    }
  }
```


