## 예외 처리
- 크게 2가지 예외
  - 개발자가 의도한 오류 `custom exception`
  - 예상치 못한 오류 `system exception`
- ✔ api 오류 메시지에 대해 일관된 형식으로 응답하도록 설계!

### 개발 순서
> [참고 자료](https://leeys.tistory.com/30?category=704916)
1. 에러 응답 모델 생성
2. 에러 `Enum Class` 선언
3. `Custom` 에러 구현

---
## 정리 ✔
### 프로그램 오류(에러)
- 프로그램 실행 중 오작동을 하거나 비정상적으로 종료되는 결과를 초래하는 원인

|에러 명|설명|
|--------|-----|
|`컴파일 에러`|컴파일 시에 발생하는 에러(소스코드의 오타나 잘못된 구문, 자료형 체크 등 기본적인 검사 수행)|
|`런타임 에러`|실행 시에 발생하는 에러 ✔|
|`논리적 에러`|실행은 되지만 의도와는 다르게 동작하는 에러|

- ✔ 자바에서는 실행 시 발생할 수 있는 오류 ✔ >> `error` `exception` 2가지 분류
  - error: __프로그램 코드에 의해서__ 수습될 수 없는 심각한 오류(예. 메모리 부족, 스택오버플로우)
  - exception: __프로그램 코드에 의해서__ 수습 가능한 다소 미약한 오류 ✌

### `Exception` `RuntimeException`
#### `Exception(Checked Exception)`
- 모든 예외의 최고 조상
- 사용자의 실수와 같은 외적인 요인에 의해 발생하는 예외
- Exception 상속받는 예외중 `RuntimeException`을 제외한 모든 예외

#### `RuntimeException(Unchecked Exception)`
- 프로그래머의 실수로 발생하는 예외 ✔
- 예. ArrayIndexOutOfBoundsException, NullPointerException, ArithmeticException

### 예외 처리하기 
- `try-catch`
- `printStackTrace()`
  - 예외발생 당시의 호출스택에 있었던 메서드의 정보와 예외 메서드를 화면에 출력
- `getMessage()`
  - 발생한 예외클래스의 인스턴스에 저장된 메시지를 얻을 수 있다.
- 멀티 catch 블럭
```java
try{
    ...
}catch(ExceptionA | ExceptionB e){
    e.printStackTrace();
}
```
- finally 블럭
  - 무조건 실행
### 예외처리하기(`Method`에 예외 처리)
```java
class ExceptionEx{
    public static void main(String[] args) throws Exception{
        method1();
    }
    static void method1() throws Exception{
        method2();
    }
    static void method2() throws Exception{
        throw new Exception();
    }
}
```

### 사용자정의 예외
- 필요에 따라 예외 클래스 선택 가능하지만!! 보통 `Exception` `RuntimeException` 클래스 상속 ✔

### 예외 되던지기
- 한 메서드에 발생할 수 있는 예외가 여럿일 때, 몇 개는 try-catch문을 통해서 메소드내에서 자체적으로 처리하고, 나머지는 선언부에 지정하여 호출한 메서드에서 처리하도록 함

### 연결된 예외
- 한 예외가 다른 예외 발생
- 반드시 예외처리를 해야하는 Exception을 RuntimeException으로 감싸 `unchecked` 가 될수 있음.
```java
static void startInstall() throws SpaceException, MemoryException{
    if(!enoughSpace()) throw new SpaceException("설치공간부족");
    if(!enoughMemory()) throw new RuntimeException(new MemoryException("메모리 부족"));
```
