## `Mockito` doReturn / thenReturn
> [참고자료](https://royleej9.tistory.com/entry/Mockito-doReturn-thenReturn)

### 공통
- 테스트 대상 기능 중 일부 기능이 준비 되지 않았을 때
- ✔다른 시스템과 통신등이 필요한 경우 `미리 리턴값 선언` 하여 테스트 가능

### 차이점
#### ⭐`thenReturn`
> 작업이 오래걸리는 경우 / 다른 시스템과의 연동 대체로 사용
- `메소드 실제 호출 o` >> 리턴값 임의로 지정 가능
- 메소드 작업 오래 걸릴 경우 대기
- 실제 메소드 호출 >> 문제 발견
#### ⭐`doReturn` 
- `메소드 실제 호출 x` >> 리턴 값 임의로 지정 가능
- 실제 메소드 호출 x >> 대상 메소드 문제 파악 어려움


```java
when(spyWhenService.callServiceAPI("2")).thenReturn(false);
doReturn(true).when(spyWhenService).callServiceAPI("1");
```
