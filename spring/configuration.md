## @ConfigurationProperties
> [참고자료](https://brush-up.github.io/java/java-ConfigurationProperties/)
- 외부 설정에 정의된 속성에 대해 쉽게 사용할수있음


### 속성
```
game-info:
games:
  AA: infoA
  BB: infoB
adUrl:
  AA: URLA
  BB: URLB
```

### 자바코드
```java
@Data
@Component
@ConfigurationProperties(value="game-info")
@Validated
public class GameInfoProperties {

    @NotNull
    private Map<String, String> games;

    @NotNull
    private Map<String, String> adUrl;

    public String getGameString(final String gameId) {
        return games.get(gameId);
    }

    public String getAdUrl(final String gameId) {
        return adUrl.get(gameId);
    }
}

```
