## 예외처리 `Exception`
> [참고 자료](https://www.nextree.co.kr/p3239/) <br>
> [예외 처리에 대한 6가지 화두](https://okky.kr/article/362305)

### 1. 예외? 
- `Error` 오류 😁
  - 시스템이 비정상적인 상황이 생겼을 때 발생
  - __시스템 레벨__ 에서 발생하기에 개발자가 미리 예측 불 >> 애플리케이션에서 오류에 대한 처리 신경 아써도 됨
- `Exception` 예외 😁
  - 개발자가 __구현한 로직__ 에서 발생
  - 발생할 상황을 미리 예측하여 처리 가능 ✔

### 2. 예외클래스
![image](https://user-images.githubusercontent.com/61215550/165218315-06b9ae31-8fdd-441c-a84a-7f8c402f272b.png)
- `Error`: 시스템 레벨의 심각한 수준의 에러 >> 시스템에 변화를 주어 문제를 처리해야 하는 경우 일반적
- `Exception`: 개발자가 로직 추가하여 처리

### 3. `Checked Exception` 과 `Unchecked(Runtime) Exception`
|목록|`Checked Exception`|`Unchecked Exception`|
|-----|---------------------|---------------------|
|처리여부⭐|반드시 예외 처리|명시적인 처리를 강제하지 않음|
|확인시점|컴파일 단계|실행단계|
|예외발생시<br>트랜잭션 처리⭐|roll-back 하지 않음|roll-back 함|
|대표예외|Exception의 상속받는 하위 클래스 중 Runtime Exception을 제외한 모든 예외<BR>- `IOException` <br>- `SQLException`|RuntimeException 하위 예외<br>- `NullPointerException` <br>- `IllegalArgumentException` <br>- `IndexOutOfBoundException` <br>- `SystemException`|

- `Checked Exception`: 컴파일 단계에서 명확하게 Exception 체크 가능한 것
- `Unchecked Exception`: 실행과정 중  어떠한 논리에 의해 발견되는 Exception / 컴파일 단계에서 확인할 수 없는 예외ㅠ.ㅠ 
  - 실행과정 중 발견된다고 해서 `Runtime Exception` ✔
- 전파방식(propagation behavior), 롤백규칙

### 4. 예외 처리 방법
- 크게 3가지
  1. 예외복구
  2. 예외처리 회피
  3. 예외 전환
  
![image](https://user-images.githubusercontent.com/61215550/165220046-e4524a90-21ee-48c0-a51a-32ccea9e9a84.png)

#### 4.1 예외복구
- 재시도를 통해 예외를 복구하는 코드
- 예외복구의 핵심 >> 예외 발생하여도 애플리케이션은 정상적인 흐름으로 진행! ✔
```java
int maxretry = MAX_RETRY;
while(maxretry -- > 0){
  try{
    //에외 발생할 가능성이 있는 코드
    return; //작업성공시 리턴
  }
  catch(SomeException e){
    //로그 출력. 정해진 시간만큼 대기
  }
  finally{
    //리소스 반납 및 정리 작업
  }
}
throw new RetryFailedException(); //최대 재시도 횟수를 넘기면 직접 예외 발생
```
  
#### 4.2 예외처리 회피
- 간단하지만 아주 신중해야 된다. // 그 처리를 회피하는 것
- 이 예외를 던지는 것이 최선의 방법이라는 확신이 있을 때만 사용
  
```java
public void add() throws SQLException{
  ... // 구현 로직
}
```
  
#### 4.3 예외 전환
- 예외를 잡아서 다른 예외를 던지는 것

```java
catch(SQLException e){
  ...
  throw DuplicateUserIdException();
}
```
