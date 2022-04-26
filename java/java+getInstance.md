## `getInstance()`
- 인스턴스 만드는 것
- `getInstance()` >> 최초의 할당된 __하나의 메모리를__ 계속 쓰는 방식 ✔

```java
package instance;

public class Test {
    static class A{
        static A instance;
        private A(){}

        public static A getInstance(){
            if(instance == null){
                instance = new A();
            }
            return instance;
        }
    }

   static class B{
        public B() {}
    }

    public static void main(String[] args) {
        A a1 = A.getInstance();
        A a2 = A.getInstance();
        A a3 = A.getInstance();

        System.out.println(a1);
        System.out.println(a2);
        System.out.println(a3);

        B b1 = new B();
        B b2 = new B();
        B b3 = new B();

        System.out.println(b1);
        System.out.println(b2);
        System.out.println(b3);
    }

}

instance.Test$A@58ceff1 ✔
instance.Test$A@58ceff1 ✔
instance.Test$A@58ceff1 ✔
instance.Test$B@49e4cb85
instance.Test$B@2133c8f8
instance.Test$B@43a25848

```
### 위와 같이 2개의 차이를 볼 수 있다!! ✔

## `new()` vs `getInstance()` 차이 ⭐
- `new()`: 객체 계속해서 생성 가능
- `getInstance()`: 싱글톤 패턴, 하나의 인스턴스만 가지고 공유
