## `private final` vs `private static final`
- private final
  - 생성자를 통해 값을 참조  
  - 해당 필드, 메서드 별로 호출할 때마다 새로이 값이 할당(인스턴스화) ✔
- private static final 
  - 생성자 참조 x / 변수는 무조건 초기화 >> 절대 해당 값을 바꾸지 않겠다는 의미 
  - 메모리에 한번 올라가면 클래스 내부의 전체 필드, 메서드에서 공유 ✔

### (추가) `static` `final` `static final`
#### 1. static
- 고정된
- 객체 생성 없이 사용할 수 있는 필드와 메소드 생성하고자 할 때 활용
#### 2. final
- 최종적인
- 해당 변수는 값이 저장되면 최종적인 값!! >> 수정 불가
- 값 저장 방법 2가지
  - 선언과 동시에 값 저장
  - 생성자 이용
#### 3. static final
- 고정된 + 최종적인
- 해당 값은 객체마다 저장될 필요 없으며(`static`) + 여러 값을 가질 수 없다(`inal`)

![image](https://user-images.githubusercontent.com/61215550/183317029-6e2148f7-9977-4ed4-8e2f-6ba00ade5e9c.png)
