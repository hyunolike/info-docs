## `PropertySourcesPlaceholderConfigurer` 프로퍼티 파일값 읽기
> [참고 자료](https://emunhi.com/view/201807/21165543909)
### `JAVA Config` 에서 읽어오기
```java
@Configuration
@PropertySource("classpath:com/config/${spring.profiles.active}/application.properties")
public class AppConfig {
   @Bean
   public static PropertySourcesPlaceholderConfigurer propertyConfigInDev() {
         return new PropertySourcesPlaceholderConfigurer();
   }
}
```
