## 객체지향설계 - 추상클래스 & 인터페이스
![image](https://user-images.githubusercontent.com/61215550/207777090-124eae5f-ed08-4457-be7e-eb2c993bb22a.png)


```java
abstract class House {
    private String roof = "House roof";
    private String wall = "House wall";
    private Door door;

    void setDoor(Door door){
        this.door = door;
    }

    Door getDoor() {
        return door;
    }

    void openDoor() {
        System.out.println("Basic door opened");
    }

    void closeDoor() {
        System.out.println("Basic door closed");
    }
}

interface Door {
    void openDoor();
    void closeDoor();
}

class BasicHouse extends House {

}

class MyHouse extends House {
    @Override
    void openDoor() {
        getDoor().openDoor();
    }

    @Override
    void closeDoor() {
        getDoor().closeDoor();
    }
}

class MyDoor implements Door{

    @Override
    public void openDoor() {
        System.out.println("My Door opened");
    }

    @Override
    public void closeDoor() {
        System.out.println("My Door closed");
    }
}

public class Abstract {
    public static void main(String[] args) {
        House basicHouse = new BasicHouse();

        basicHouse.openDoor();
        basicHouse.closeDoor();

        House myHouse = new MyHouse();
        Door myDoor = new MyDoor();

        myHouse.setDoor(myDoor);

        myHouse.openDoor();
        myHouse.closeDoor();
    }
}
```
