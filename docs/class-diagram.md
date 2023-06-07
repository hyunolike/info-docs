## `UML` 클래스 다이어그램
> [참고자료](https://gmlwjd9405.github.io/2018/07/04/class-diagram.html) <br>
> [참고자료](https://brownbears.tistory.com/577)
- 구조 다이어그램 
- 클래스 내부 구성요소 및 클래스 간의 관계 도식화 >> 시스템의 특정 모듈이나 일부 및 전체 구조화
- 목적별 3가지 😛 >> 명세/구현 (개발 직전 설계 & 구현 이후 설명 목적)
  - 개념`
  - `명세`
  - `구현`

### 요소
#### 클래스
- 이름, 속성(변수), 메소드 순으로 나열
  - 속성, 메소드 생략 가능
##### ⭐클래스간 관계
> 리엑트 >> `Composition` 사용할꺼야
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/7cd3b965-631c-460b-b9c4-952f709e0033)
##### 관계별 설명
|관계|설명|
|--|--|
|`Association`|다른 객체 참조|
|`Inheritance`|상속 관계 / 일반화 (Generalization)|
|`Realization`|인터페이스 상속 >> 클래스 실제 기능 실현화|
|`Dependency`|클래스간 참조 관계 / 🙄 `Associaition과의 차이는`? |
|`Aggregation`|집합 관계|
|`Composition`|전체 - 부분의 집합 관계|

