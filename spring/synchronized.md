## 자바 스레드 동기화
> [참고자료](https://kadosholy.tistory.com/123)

### 스레드 동기화
- 멀티스레드 환경에서 여러 스레드 >> **하나의 공유자원** 동시에 접근하지 못하도록 막는 것
- 임계영역 >> 공유데이터가 사용되어 동기화가 필요한 부분
  - `synchronized` 키워드 사용해 여러 스레드 동시에 접근하는 것을 금지! >> 동기화 가능✔

### 사용 방법 `synchronized`
- `synchronized` 키워드 사용해 임계영역 지정!
- lock 걸림으로써 다른 스레드 접근 x
  - lock 해당 객체당 하나씩 존재! 
  - 임계영역 지정된 코드는 lock 권한을 얻은 하나의 객체만이 독점적으로 사용 가능


```java
void increase() {
	synchronized(this) {
		count++;
	}
	System.out.println(count);
}
```

