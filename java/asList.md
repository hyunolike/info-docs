## `Arrays.asList()` vs `List.of`
- 자바 Array >> List 변환하기 위해선 `Arrays.asList(array)` 사용
- `Java 9` 부터 `List.of(array)` 새로운 팩토리 메소드 도입

### 차이
1. 변경 가능 여부(`Mutable` / `Immutable`)
  - `Arrays.asList()`: 반환된 list 변경 가능: ArrayList 반환 및 set 등으로 구현
  - `List.of()`: 변경 불가: ListN 타입 객체 반환(불변 객체)
  - (추가) Arrays.asList() >> Arrays 내부 클래스 !! 따라서, add, remove 구현되어 있지 않음
2. `Null` 허용 여부
  - `Arrays.asList()`: null 허용
  - `List.of()`: 반환 객체 생성될 때 내부적으로 null 체크하고 null 허용하지 않음

3. 참조 / 비참조
  - `Arrays.asList(array)`: 참조 사용 > 배열의 크기 늘리거나 줄일 수 없음 
  - `List.of(array)`: 값 기반 > 독립적인 객체 생성하기에 참조 일어나지 않음

4. 메모리 사용
  - `Arrays.asList()`: 힙에 더 많은 객체 생성(오버헤드 공간 많이 차지) 
  - `List.of()`: 단지 값 요소
  

