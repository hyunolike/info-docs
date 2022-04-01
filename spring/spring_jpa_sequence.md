## 스프링에서 오라클 시퀀스 사용방법
- Oracle의 Sequnce 이용해 `PK` 자동 증가

```JAVA
@Id
@SequenceGenerator(name="시퀀스 생성자 이름", sequenceName="내가 만든 시퀀스 생성자 명", allocationSize = 1)
@GeneratedValue(strategy=GenerationType.SEQUENCE, generator="시퀀스 생성자 이름")
private long id;
```
