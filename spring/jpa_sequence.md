## `JPA` 식별자 할당 사용 전략
> [참고자료](https://dololak.tistory.com/479)
### JPA 식별자
- 엔티티: 논리적인 공간인 영속성 콘텍스트에서 관리
  - 엔티티 구분할 수 있는 식별자 필요!
- 엔티티가 영속성 콘텍스트에 들어가 JPA에 관리되는 시점 >> 반드시 식별자로 지정된 필드에 __식별자 값__ 할당!!! ✔

### `SEQUENCE` 전략
- `Oracle` `DB2` `H2` `PostgreSQL` 등에서 사용할 수 있는 시퀀스 기능을 활용한 ⭐`SEQUENCE` 전략 !!
- DB에서 __시퀀스 기능__ 지원해야만 사용가능한 전략
- ✔ `DBMS` 종속적인 식별자 할당 전략

#### 생성 로직
1. USER 테이블 생성
```SQL
CREATE TABLE user (
    ID BIGINT  NOT NULL PRIMARY KEY ,
    NAME VARCHAR(255)
);
 
 
CREATE SEQUENCE USER_SEQ START WITH 1 INCREMENT BY 1;   
```
2. USER 테이블과 시퀀스 바탕으로 User 엔티티 클래스에서 전략 설정
```sql
@Entity
@SequenceGenerator(
            name="USER_SEQ_GEN", //시퀀스 제너레이터 이름
            sequenceName="USER_SEQ", //시퀀스 이름
            initialValue=1, //시작값
            allocationSize=1 //메모리를 통해 할당할 범위 사이즈
            )
public class User {
 
 
    @Id
    @GeneratedValue(
            strategy=GenerationType.SEQUENCE, //사용할 전략을 시퀀스로  선택
            generator="USER_SEQ_GEN" //식별자 생성기를 설정해놓은  USER_SEQ_GEN으로 설정        
            )
    private Long id;
 
 
    private String name;
 
 
    public Long getId() {
        return id;
    }
 
 
    public String getName() {
        return name;
    }
 
 
    public void setName(String name) {
        this.name = name;
    }
}
```

#### 시퀀스 생성기 설정
```sql
@SequenceGenerator(
            name="USER_SEQ_GEN", //시퀀스 제너레이터 이름
            sequenceName="USER_SEQ", //시퀀스 이름
            initialValue=1, //시작값
            allocationSize=1 //메모리를 통해 할당할 범위 사이즈                                
            )
```
