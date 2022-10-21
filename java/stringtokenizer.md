## `StringTokenizer` 문자열 분리
> [참고자료](https://jhnyang.tistory.com/398)
- ✔ `BufferedReader` 클래스의 메소드로 입력 읽게 되면 >> **라인 단위**
  - 컴마, 특정 문자에 따라 문자열 나누고 싶을 때 >> StringTokenizer 이용 가능
- ⭐`String`: 문자열을 
- ⭐`Tokenizer`: 토큰화한다.
- ![image](https://user-images.githubusercontent.com/61215550/197105257-dd5dd39c-b4b9-4442-a0a5-8b5cbc1df1d5.png)


```java
public class Test {
    public static void main(String[] args) {
        String str = "안녕 하 세 요오오오오오";
        StringTokenizer st = new StringTokenizer(str);
        while(st.hasMoreTokens()){
            System.out.println(st.nextToken());
        }
    }
}
```

### 메서드 
|메서드명|설명|
|--------|-----|
|boolean hasMoreTokens()|남아있는 토큰 있으면 true 리턴, 더 이상 토큰 없으면 false 리턴|
|String nextToken()|객체에서 다음 토큰을 반환|
|String nextToken(String delim)|delim 기준으로 다음 토큰 반환|
|boolean hasMoreElements()|element보다 토큰으로 된 메소드를 주로 씀 / 그 위에 있는 거랑 같은 기능|
|Object nextElement()|문자열이 아닌 객체 리턴|
|int countTokens()|총 토큰의 개수 리턴|

### 예제 - 각 특정 문자로 구분해서 배열에 저장하기 
```java
public class Test {
    public static void main(String[] args) {
        String str = "안녕++하,세|요오오오오오";
        StringTokenizer st = new StringTokenizer(str, "+,|");
        List sts = new ArrayList();

        while(st.hasMoreTokens()){
            sts.add(st.nextToken());
        }

        System.out.println(sts);
    }
}
```
