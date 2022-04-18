## Entity와 EntityManager와 EntityManagerFactory
> 개발자가 그 내부를 들여다 볼수 없기에 약간은 논리적이거나 추상적인 개념으로 바라보자!! ✌ <br>
> [참고 자료](https://perfectacle.github.io/2018/01/14/jpa-entity-manager-factory/)
### `Entity`
- `DB` 의 테이블과 매칭이 되는 개념
- 여러개의 엔티티 생성이 가능하다!
- `JPA`를 잘 다룬다면 1개의 엔티티로도 충분히 커버 가능

### `EntityManager`
- 엔티티를 관리하는 역할을 수행하는 클래스 ✔
- ![image](https://user-images.githubusercontent.com/61215550/163755900-c86836c3-ad79-4ffc-97dd-0a4666d17f44.png)
- 엔티티 내부에 __영속성 컨텍스트__ 라는 걸 두어 엔티티들 관리!!
#### 영속성 ⭐
- 기본적으로 컴퓨터 공학에서는 __비휘발성__ 
- 휘발성은 프로그램 꺼지거나 전원 나가면 데이터 날라가지만 비휘발성은 정반대!
#### 컨텍스트 ⭐
- 하나의 환경, 공간쯤으로 이해하자
#### 영속성 컨텍스트 ⭐
- 엔티티를 영구히 저장하는 환경 
- 영속성 컨텍스트를 관리하는 모든 엔티티 매니저가 초기화 및 종료되지 않는 한 엔티티를 영구히 저장하는 환경

### 엔티티 매니저와 영속성 컨텍스트의 엔티티 관리 
```java
public class Join {
    public void join(String name, int age) {
        // 아직까지는 해당 엔티티를 엔티티 매니저가 관리하지 않는다.
        Member member = new Member();
        member.setName(name);
        member.setAge(age);
        
        // 엔티티 매니저가 있다고 가정.
        // 추후에 엔티티 매니저 팩토리와 함께 엔티티 매니저를 어떻게 생성하는지 설명.
        EntityManager em;
        EntityTransaction tx = em.getTransaction();
        
        try {
            // 엔티티 매니저에서 수행하는 모든 로직은 트랜잭선 안에서 수행돼야 한다.
            tx.begin();
            
            // 이렇게 하면 해당 엔티티 매니저의 영속성 컨텍스트에 위에서 만든 member 객체가 저장된다.  
            // 이제 member 엔티티는 엔티티 매니저의 관리 대상이 되고, 영속성을 가졌다고 말할 수 있다.
            em.persist(member);
            
            // 트랜잭션을 커밋한다.
            tx.commit();
        } catch(Exception e) {
            // 어떤 이유에서 오류가 났다면 트랜잭션을 롤백 시켜줘야한다.
            tx.rollback();
        } finally {
            // 엔티티 매니저를 종료시켜줘야 한다.  
            // 아마 더 이상 사용하지 않는 자원이므로 더 이상 사용하지 않는 자원이라고 표시하는 것 같다.
            // 그럼 아마 GC가 해당 엔티티 매니저 자원을 수거해가서 메모리에 반환하지 않을까??
            // 성능 상 문제가 있어서 이렇게 종료시켜줘야 하는 건지 모르겠다. 
            em.close();
        }
    }
}
```
- 추가적으로 궁금해진 2가지 개념 `엔티티 생명주기` `트랜잭션`

### 트랜잭션
- 하나의 작업 단위
- ![image](https://user-images.githubusercontent.com/61215550/163756334-e4f66d58-aa95-48c8-8d6f-211397f1bc18.png)
#### 왜 `JPA`는 트랜잭션 안에서 수행하는 걸까?
- 쓰기 지연 SQL 저장소 ✔
- ![image](https://user-images.githubusercontent.com/61215550/163756467-b2fa0248-19a4-4b4a-a9e3-a86e26dca058.png)

### `EntityManagerFactory`
- 엔티티 매니저는 여러 스레드가 동시에 접근하면 __동시성 문제__ 가 발생하므로 스레드 간에 절대 공유하면 안됨!
