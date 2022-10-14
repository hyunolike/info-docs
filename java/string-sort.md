## 자바 문자열 정렬
> [참고자료](https://www.techiedelight.com/ko/sort-string-java/)
- ✅문자열은 자바에서 `불변` !!! 

### 방법1. Arrays.sorted()
```java
import java.util.Arrays;
 
class Main
{
    public static void main(String[] args)
    {
        String str = "CADB";
 
        char[] chars = str.toCharArray();
        Arrays.sort(chars);
        str = new String(chars);
 
        System.out.println(str);
    }
}
```

### 방법2. Java 8 
```java

class Main
{
    public static void main(String[] args)
    {
        String str = "CADB";
 
        str = str.chars()        // IntStream
                .sorted()
                .collect(StringBuilder::new,
                        StringBuilder::appendCodePoint,
                        StringBuilder::append)
                .toString();
 
        System.out.println(str);
    }
```


```java

import java.util.stream.Collectors;
import java.util.stream.Stream;
 
class Main
{
    public static void main(String[] args)
    {
        String str = "CADB";
 
        str = Stream.of(str.split(""))
                    .sorted()
                    .collect(Collectors.joining());
 
        System.out.println(str);
    }
}
```
