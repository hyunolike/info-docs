## `H2 웹 콘솔`
> [H2 공식 페이지](https://www.h2database.com/html/main.html)
- 기본적으로 웹 콘솔 지원
- 스프링 부트에서는 2가지 방법으로 활성화 가능
  1. `spring-boot-devtools` 적용
  2. application.yml >> `spring.h2.console.enabled=true` 적용

### 웹 콘솔 구조
- 아래 그림과 같이 콘솔은 웹에서만 동작 가능!! ⭐
  - 웹 브라우저가 아닌 다른 클라이언트로부터의 접근 불가능
  - 따라서 Intellij와 같은 다른 클라이언트에서 접근하려면 `H2 TCP` 서버 별도 구축해야됨
![image](https://user-images.githubusercontent.com/61215550/170910075-8c3faaac-140e-48b3-bbda-ea17d71e722e.png)
![image](https://user-images.githubusercontent.com/61215550/170910215-7646eef1-3c4f-4fbd-a1f0-92740cd87698.png)

### H2 TCP 서버 생성 ✔ 
#### 1. H2 TCP 서버 구동하기 위해선 `runtimeOnly` 로만 사용 불가 >> `complie` 로 변경해주자 
- ![image](https://user-images.githubusercontent.com/61215550/170910312-97e3dec0-2c4d-48a1-8a54-12a4b5e30523.png)
- ![image](https://user-images.githubusercontent.com/61215550/170910455-ade58057-af3c-4bb7-a3d3-4471040989d6.png)

#### 2. H2 TCP 서버 구동 빈 추가
- H2 TCP 서버 기본 포트: 9092
- 스프링부트 애플리케이션 실행하면 함께 구동되고 종료되면 함께 종료
```java
@Configuration
public class H2ServerConfig {

    @Bean
    public Server h2TcpServer() throws SQLException {
        return Server.createTcpServer().start();
    }
}
```
