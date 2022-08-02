## final
> [참고자료](https://sabarada.tistory.com/148)
- `final`: 무언가 제한!!

### final로 선언한 인스턴스 변수
- final 선언 변수 >> 변경 불가 상수
- 변수 선언 시 >> **선언 + 초기화** 동시 진행
  - ✔ final 선언 인스턴스 변수 >> 예외적으로 **생성자에서** 초기화 가능!!
  - 생성자로부터 받은 매개변수로 인스턴스변수 초기화 !!

```java
⭐ final >> 매번 새로운 인스턴스 생성!!

final class Distance{
  final DistanceUnit unit;
  final double value;
  
  Distance(DistanceUnit unit, double value){
    this.unit = unit;
    this.value = value;
  }
  
  Distance add(Distance distance){
    return new Distance(unit, value + distance.converTo(unit).value); ⭐
  }
  
  Distance converTo(DistanceUnit otherUnit){
    double conversionRate = unit.getConversionRate(otherUnit); ⭐
    return new Distance(otherUnit, conversionRate * value);
  }
}
```
