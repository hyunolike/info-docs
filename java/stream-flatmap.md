## 자바 `Stream API` `map vs flatMap`
> [참고자료](https://devjem.tistory.com/41)
- ✅ `flatMap()`: 중복된 스트림 `1차원`으로 평면화 시키는 것

### 비교
```java
String[] animal = ["cat","dog"];

⭐️ map
List<String[]> results = animals.stream().map(animal -> animal.split(""))
                                .collect(Collectors.toList());
결과 > [  [  "c", "a", "t"  ] , [ "d", "o", "g" ]  ]    

⭐️ flatMap
List<String> results = animals.stream().map(animal -> animal.split(""))
        .flatMap(Arrays::stream)
        .collect(Collectors.toList());

results = [c, a, t, d, o, g]
```

### 결론
- `flatMap` 사용하면 **중복 구조** 로 되어있는 리스트 >> `하나의 스트림` 처럼 다룰 수 있다!
