## 자바 스트림
- 데이터 처리 간결하게 표현 가능

### 1. 스트림 생성
- `Collection` >> stream()
```java
List<String> list = Arrays.asList("a", "b", "c");
Stream<String> stream = list.stream();
```

- `Array` >> Arrays.stream()
```java
String[] array = new String[]{"a", "b", "c"};
Stream<String> stream = Arrays.stream(array, 1, 3); // {"b", "c"}
```

- `Builder` 
```java
Stream<String> stream = Stream<String>builder()
                          .add("A")
                          .add("B")
                          .build();
```

- `Generator`
```java
Stream<String> stream = Stream.generate(() -> "Hello").limit(5);
```

- `Iterator`
```java
Stream<String> stream = Stream.iterate(100, n -> n+10).limit(5);
```

...

