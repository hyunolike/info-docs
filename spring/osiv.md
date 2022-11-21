## OSIV
> [참고자료](https://incheol-jung.gitbook.io/docs/q-and-a/spring/osiv)
- ![image](https://user-images.githubusercontent.com/61215550/202960424-5064282c-2769-4b64-8405-084ee1d65c09.png)

### OSIV란
- ✔ `View` 영역까지 Session 영역이 열어 둔다는 의미!
- `Open Session`: 영속성 컨텍스트의 영역
- `View`: 우리가 생각하는 Controller 영역 / 뷰 영역(jsp, typmeleaf)
- 😛 그니까, 컨트롤로나 뷰 영역에서도 __영속성 컨텍스트__ 유지한다는 것!

### 단점 ㅠ,ㅠ 
```java
@GetMapping
public Person get(){
    Person person = personService.get(1);
    person.setName("steve");
    Person person2 = personService.get(1);
    return person;
}
```


- 왜 변경?? `dirty check` 때문! 
#### 1. 영속성 컨텍스트를 여러 트랜잭션이 공유할 수 있다는 것 주의
#### 2. 프리젠테이션 계층에서 여러 엔티티를 수정 하고나서 비즈니스 로직을 수행하면 엔티티 수정될 수 있음
#### 3. 프리젠테이션 계층에서 지연 로딩에 의한 sql 실행 ㅠ,ㅠ >> 성능 튜닝 시에 확인해야 할 부분 넓어져..
