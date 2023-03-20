## DTO 전략 
> [DTO를 inner class로 관리하기](https://unluckyjung.github.io/dev/2022/02/20/Dto-InnerClass/) <BR>
> [Entity to DTO, DTO to Entity 그리고 ModelMapper](https://dbbymoon.tistory.com/4) <BR>
> [DTO에 관한 생각](https://velog.io/@aidenshin/DTO%EC%97%90-%EA%B4%80%ED%95%9C-%EA%B3%A0%EC%B0%B0)  
- ![image](https://user-images.githubusercontent.com/61215550/226225459-6ca185cc-a42b-47a5-a0f9-61dc16a76add.png)
  
### Entity 클래스
- `JPA` 실제 데이터베이스의 테이블과 매칭되는 클래스  

### 요청별 DTO 이너 클래스로 관리
```JAVA
@Getter
@NoArgsConstructor(access = AccessLevel.PROTECTED)
@Entity
public class Member {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    public Member(final String name) {
        this.name = name;
    }

    @Getter
    @AllArgsConstructor
    @NoArgsConstructor
    public static class Request {
        private String name;
    }

    @Getter
    @AllArgsConstructor
    public static class Response {
        private Long id;
        private String name;
    }
}  
```
  
