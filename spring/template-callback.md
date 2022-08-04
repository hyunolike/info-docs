## Template Callback Pattern
> [참고자료](https://steady-coding.tistory.com/588) <br>
> [참고자료](https://velog.io/@dbsrud11/SpringBoot-%ED%95%B5%EC%8B%AC-%EC%9B%90%EB%A6%AC-%ED%85%9C%ED%94%8C%EB%A6%BF-%EB%A9%94%EC%86%8C%EB%93%9C-%ED%8C%A8%ED%84%B4%EA%B3%BC-%EC%BD%9C%EB%B0%B1-%ED%8C%A8%ED%84%B4-3)<br>
> 템플릿: 정해져 있는 틀 / 콜백: 다른 코드의 인수로서 넘겨주는 실행 가능한 코드, 어떤 이벤트에 의해 호출되어지는 코드

- ✔전략 패턴의 변형된 형태(보완)
  - 기존, 매번 클래스 생성 >> 구체 클래스 주입 
  - ✔ 템플릿 콜백 >> 독립된 클래스 ❌ / 익명 내부 클래스 생성 >> 활용 및 주입
- ![image](https://user-images.githubusercontent.com/61215550/182773658-3869a157-4983-4d94-86ce-415747be2fd5.png)

### 1. Template
- 어떤 목적을 위해 미리 만들어둔 틀 >> 고정된 틀 안에 바꿀 수 있는 부분 넣어서 효율적으로 사용!
- 고정된 작업 흐름을 가진 코드 재사용 시 유용!
- `Template/Callback` 패턴 >> `Callback` 오브젝트 받는 곳 ✔


### 2. Callback
- 다른 오브젝트 실행되는 것 목적 >> 다른 오브젝트의 메소드에 전달하는 오브젝트(주로 파라미터로 통해 전달)
- 콜백 오브젝트의 메소드 실행시키기 위한 목적으로 사용!
- 일반적으로 하나의 메소드를 가진 인터페이스를 구현한 익명 내부 클래스로 만들어짐


|흐름|
|----|
|![image](https://user-images.githubusercontent.com/61215550/182775357-808fd28a-764c-446f-95d7-4cd91c4de4e8.png)|

---

### 1. 기존 코드
```java
public interface Strategy {
  public abstract void ChoosePen();
}

public class Student{ 
  public void takeNotes(Strategy strategy){  ✔
    strategy.ChoosePen();
  }
}

public class Teacher{
  public static void main(String[] args) {
          Student student = new Student();

          student.takeNotes(new Strategy() {
              public void ChoosePen() {
                  System.out.println("검은펜을 잡았습니다.");
              }
          });

          student.takeNotes(new Strategy() {
              public void ChoosePen() {
                  System.out.println("빨간펜을 잡았습니다.");
              }
          });

          student.takeNotes(new Strategy() {
              public void ChoosePen() {
                  System.out.println("파란펜을 잡았습니다.");
              }
          });
      }  
}
```

### 2. 템플릿 콜백 패턴
```java
public class Student {
    public void takeNotes(String Pen) {
        System.out.println("=== 선생님께서 펜을 주십니다. ===");
        takePen(Pen).ChoosePen(); ⭐
        System.out.println("필기를 시작합니다.");
    }

    private Strategy takePen(String Pen) {
        return new Strategy() {
            @Override
            public void ChoosePen() {
                System.out.println(Pen + "을 잡았습니다.");
            }
        };
    }
}

public class Teacher {
    public static void main(String[] args) {
        Student student = new Student();

        student.takeNotes("검정펜"); ⭐
        student.takeNotes("빨간펜"); ⭐
        student.takeNotes("파란펜"); ⭐
        student.takeNotes("무지개 형관펜"); ⭐
    }
}
```
