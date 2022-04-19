## `JPA` `Hibernate` `Spring Data JPA`
### `JPA` = 기술 명세
- Java Persistence API의 약자
- 자바 어플리케이션에서 관계형 데이터베이스를 사용하는 방식을 정의한 인터페이스
- 라이브러리 x / 인터페이스 o
- 일반적인 백엔드 api가 클라이언트가 어떻게 서버를 사용해야 하는지를 정의한 것 처럼!!
- 단순 정의니까 구현이 없다. 

```JAVA
package javax.persistence;

import ...

public interface EntityManager {

    public void persist(Object entity);

    public <T> T merge(T entity);

    public void remove(Object entity);

    public <T> T find(Class<T> entityClass, Object primaryKey);

    // More interface methods...
}
```


### `Hibernate` = JPA의 구현체
- 마치 자바의 interface와 해당 interface를 구현한 class와 같은 관계
- ![image](https://user-images.githubusercontent.com/61215550/163926152-63aca23d-6791-4d92-9e6f-9bcd8fbfeb43.png)
- ⭐ JPA를 사용하기 위해서 반드시 `Hibernate` 사용할 필요 없다.
  - Hibernate의 작동 방식이 마음에 들지 않는다면 언제든지 DataNucleus, EclipseLink 등 다른 JPA 구현체를 사용해도 되고, 심지어 본인이 직접 JPA를 구현해서 사용할 수도 있다. 다만 그렇게 하지 않는 이유는 단지 Hibernate가 굉장히 성숙한 라이브러리이기 때문일 뿐이다.

### `Spring Data JPA` = JPA 쓰기 편하게 만들어놓은 모듈
- JPA 더 쉽고 편하게 사용할 수 있도록 도와줌
- JPA를 한 단계 추상화시킨 `Repository` 라는 인터페이스를 제공함으로써 이루어짐

### 요약
![image](https://user-images.githubusercontent.com/61215550/163926482-da6756fd-6e86-456e-8fc8-079085abcf9c.png)
