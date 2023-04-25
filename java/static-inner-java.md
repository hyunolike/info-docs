## 내부 클래스는 `static` 반드시!!
> [참고자료](https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EC%9E%90%EB%B0%94%EC%9D%98-%EB%82%B4%EB%B6%80-%ED%81%B4%EB%9E%98%EC%8A%A4%EB%8A%94-static-%EC%9C%BC%EB%A1%9C-%EC%84%A0%EC%96%B8%ED%95%98%EC%9E%90)
- inner 클래스: 메모리 더 먹음 / 더 느림 / 바깥 클래스가 CG대상에서 빠져 버려 메모리 관리 불가 ㅠ,ㅠ
  - `비정적(non-static)` >> 바깥 클래스의 인스턴스와 암묵적으로 연결


```java
public class Outer_Class {
   int field = 10;
   int getField() {
       return field;
   }

   class Inner_Class {
       int inner_field = 20;
       int getOuterfield() {
           return Outer_Class.this.getField(); // 숨은 외부 참조가 있기 때문에 가능
       }
   }
}
```
### inner 클래스의 메모리 누수 현상
- ✔ 외부참조로 인한 `메모리 누수`
- 비정적 내부 클래스 >> 외부 참조로 연결 >> 제거 안됨 / 잔존 >> 메모리 누수 >> 프로그램 터짐

### ⭐ 내부 클래스 >> static 으로 선언
- static inner 클래스 >> 외부 참조 안함 !!
- 메모리 누수 없음
  - 외부 인스턴스 없이 만들 수 있음 >> 외부 참조 없음!
