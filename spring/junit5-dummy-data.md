## Spring Boot + Junit5 에서 테스트 초기 데이터 로딩
> [참고자료](https://github.com/HomoEfficio/dev-tips/blob/master/Spring-Boot-JUnit5-Initial-Data.md)
- ✔데이터 로딩하는 방법 2가지
  - 직접 코드를 작성하는 방법 - ⭐테스트 클래스 당 1번만 데이터 로딩해서 테스트 내내 사용하고 싶은 경우!!
  - `@Sql` 사용하는 방법

### 예시 코드
```java
@SpringBootTest
@Transactional
@TestInstance(TestInstance.Lifecycle.PER_CLASS)  //  (3)
class ProductReviewControllerTest {

    ...
    
    @Autowired
    private DataSource dataSource;


    @BeforeAll
    public void beforeAll() throws Exception {  // (2)
        System.out.println("BeforeAll");
        try (Connection conn = dataSource.getConnection()) {  // (2)
            ScriptUtils.executeSqlScript(conn, new ClassPathResource("/data/insert-customer-seller-product.sql"));  // (1)
        }
    }

    @AfterAll
    public void afterAll() throws Exception {
        System.out.println("AfterAll");
        try (Connection conn = dataSource.getConnection()) {
            ScriptUtils.executeSqlScript(conn, new ClassPathResource("/data/truncate-customer-seller-product.sql"));
        }
    }
    
    ...
}
```

### 예시 코드 설명
1. `dataSource` 통해 DB connection 얻어오기
2. `@BeforeAll` 에서 static 없이 주입받은 이유 >> `@TestInstance(TestInstance.Lifecycle.PER_CLASS)`
  - 새로 생성하지 않고 하나만  생성해서 테스트 클래스에 포함된 테스트 메서드가 수행되는 동안 계속 사용 가능!

  
