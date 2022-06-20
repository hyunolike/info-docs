## `winsw` 를 사용한 `Spring Boot` Window Service 등록 방법
> [참고 자료](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=jang_delay&logNo=222131244354) <br>
> [영문 참고 자료](https://eric-ndirangu.medium.com/deploying-a-springboot-application-jar-as-a-windows-service-using-winsw-75314f21d667)

### 1. `winsw` 다운로드
- `windows service wrapper` 파일 다운
- [다운로드](https://repo.jenkins-ci.org/releases/com/sun/winsw/winsw/)
- [깃허브 프로젝트 다운로드](https://github.com/winsw/winsw/releases)

### 2. 설정
1. 원하는 폴더 설정
2. 생성한 폴더에 `winsw` 파일 옮기기
3. `winsw` 파일 이름을 폴더 이름과 같게 또는 배포 파일 이름과 같게 설정(편의성)
4. 프로젝트 이름과 같은 xml 파일 생성


```xml
<?xml version="1.0" encoding="UTF-8"?>
<service>
    <id>HRHubWebService</id>
    <name>HRHubWebService</name>
    <description>HRHubWebService Windows Service</description>
    <env name="JAVA_HOME" value="D:\Program Files\ojdkbuild\java-1.8.0-openjdk-1.8.0.265-1"/>
    <executable>D:\Program Files\ojdkbuild\java-1.8.0-openjdk-1.8.0.265-1\bin\java</executable>
    <arguments>-jar "HRHUB_AK-0.0.1.war" --spring.config.location=D:\HRHub\application.properties</arguments>
    <logpath>D:\HRHub\logs</logpath>
    <logmode>rotate</logmode>
</service>
```

5. cmd 창 실행
```shell
//서비스 등록
> D:\HRHub>HRHub.exe install
2020-10-30 17:16:34,437 INFO  - Installing the service with id 'HRHubWebService'
//서비스 삭제
> D:\HRHub>HRHub.exe uninstall
2020-10-30 17:17:44,627 INFO  - Uninstalling the service with id 'HRHubWebService'
```
