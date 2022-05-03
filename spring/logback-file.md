## `logback` 로 로그 파일 생성😁
- [Spring Boot : Logger logback 설정파일 작성 및 Customization](https://kogle.tistory.com/29)
- [Spring Boot 에서 logback 사용하기](https://linkeverything.github.io/springboot/spring-logging/)

### ✔ 모든 파일은 자동으로 생성!! 폴더까지
### `example`
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<configuration scan="true" scanPeriod="60 seconds" >
    <property name="LOG_PATTERN" value="%d{HH:mm} %-5level %logger{36} - %msg%n" />
    <property name="LOG_FILE_LOCATION" value="./logs"/>
    <springProfile name="dev">
        <appender name="CONSOLE" class="dch.qos.logback.core.ConsoleAppener">
            <encoder>
                <pattern>${LOG_PATTERN}</pattern>
            </encoder>
        </appender>
        <appender name="INFO_LOG" class="ch.qos.logback.core.rolling.RollingFileAppender">
            <file>${LOG_FILE_LOCATION}/info.log</file>
            <filter class="ch.qos.logback.classic.filter.LevelFilter">
                <level>INFO</level>
                <onMatch>ACCEPT</onMatch>
                <onMismatch>DENY</onMismatch>
            </filter>
            <encoder>
                <pattern>${LOG_PATTERN}</pattern>
            </encoder>
            <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
                <fileNamePattern>${LOG_FILE_LOCATION}/logback.%d{yyyy-MM-dd}.%i.log.gz</fileNamePattern>
                <timeBasedFileNamingAndTriggeringPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedFNATP">
                    <!-- or whenever the file size reaches 100MB -->
                    <maxFileSize>100MB</maxFileSize>
                    <!-- kb, mb, gb -->
                </timeBasedFileNamingAndTriggeringPolicy>
                <maxHistory>30</maxHistory>
            </rollingPolicy>
        </appender>
        <root level="INFO">
            <appender-ref ref="CONSOLE"/>
            <appender-ref ref="INFO_LOG"/>
        </root>

        <logger name="com.hyunho.service" level="INFO">
            <appender-ref ref="INFO_LOG"/>
        </logger>

    </springProfile>
</configuration>
```
### 생성 요약
![image](https://user-images.githubusercontent.com/61215550/166407037-bc10685d-05ea-426d-b4cd-0521ccf16dcb.png)
- ⭐루트 레벨 설정 참고자료
- ![image](https://user-images.githubusercontent.com/61215550/166418451-e8392740-6385-4c8b-b6f4-0d3afa7479ea.png)

### 로그 파일 생성 전략(참고한 거)
> [참고 자료](https://github.com/Livenow14/slf4j-logback-lab/tree/springboot-logging/src/main/resources)


![image](https://user-images.githubusercontent.com/61215550/166408749-e8436331-7cfa-4909-8414-30e5ed58e5c3.png)

### 실제 로그 전략
- 개발 > 콘솔만 출력되게끔
- 운영 > 로그 파일만 생성되게끔
- ![image](https://user-images.githubusercontent.com/61215550/166411164-b0852014-8e71-46b4-88fe-55900cb123b6.png)

