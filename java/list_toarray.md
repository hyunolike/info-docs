## List의 `toArray()` 메서드 아리송한 코드??
- 기본적으로 리스트를 배열로 바꿔주는 메서드!!

```java
List<String> stringList = new ArrayList<String>(); 
stringList.add("A");
stringList.add("A");
stringList.add("A");

String[] stringArray = stringList.toArray(new String[0]); 🙄
```
### 왜 사이즈 `0`으로 명시??
1. List를 toArray 메서드에 파라미터로 넘어가는 배열 객체의 size만큼의 배열로 전환
2. 단, List size가 인자로 넘어가는 배열 객체의 size보다 클 경우, ✔ 해당 List의 size로 배열이 만들어짐
3. 반대로 해당 List size가 인자로 넘어가는 배열 객체의 size보다 작을때는, 인자로 넘어가는 배열 객체의 size로 배열이 만들어짐!!

![image](https://user-images.githubusercontent.com/61215550/162124208-16b9f5d0-9c62-4626-98e0-0a5d52850a10.png)
