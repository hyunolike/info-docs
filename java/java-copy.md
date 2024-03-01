## `copyOf` `copyOfRange` `arraycopy`
> [참고자료](https://romcanrom.tistory.com/48)


```
Arrays.copyOf()
Arrays.copyOfRange()
System.arraycopy()
```
### Arrays.copyOf()
- Arrays.copyOf(`원본배열`, `복사할 길이`)
- 지정한 배열을 인덱스 `0`부터 원하는 길이만큼 복사


```java
int[] intArr = new int {1, 2, 3, 4, 5};
int[] intArrCopy = Arrays.copyOf(intArr, 3);
for(int i : intArrCopy) System.out.println(i);

1
2
3
```
### Arrays.copyOfRange()
- Arrays.copyOfRange(`복사할 원본 배열`, `복사를 시작할 인덱스`, `복사를 끝낼 인덱스`)
- 지정한 배열에서 특정 범위만큼 요소들 복사해 `새로운 배열`로 반환
...


### 🔥결론
- 자바 배열 생성시 길이 조절 불가!! >> 두 배열을 합쳐 저장할 새 배열을 만들어 주는 것에 주의하자!
