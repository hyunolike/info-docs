## `Collection` - contains, containsAll
> [참고자료](https://priming.tistory.com/35)
- `contains` `containsAll` 모두 >> bollean 반환값

### contains
- 🔥 `Integer` 리스트면 `Integer` 타입만 사용 가능해


```java
List list = new ArrayList();
list.add(1);
list.add("2");
list.add('3');

System.out.println("list.contains(1) = " + list.contains(1));
System.out.println("list.contains(2) = " + list.contains(2));
System.out.println("list.contains('3') = " + list.contains('3'));
```
### containsAll
- `equals()` 메소드 통해 포함 여부 판별
- 인자로 주어진 컬렉션과 모두 일치해야 >> `ture` 판별!


```java
List<String> list = new ArrayList<>();
list.add("a");
list.add("b");
list.add("c");
list.add("d");
list.add("e");

Set<String> set = new HashSet<>();
set.add("b");
set.add("c");

Set<String> set2 = new HashSet<>();
set2.add("e");
set2.add("f");

System.out.println("list.containsAll(set) = " + list.containsAll(set));
System.out.println("list.containsAll(set2) = " + list.containsAll(set2));
```
