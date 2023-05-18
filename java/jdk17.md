## JDK 17 도입
> [참고자료](https://techblog.gccompany.co.kr/%EC%9A%B0%EB%A6%AC%ED%8C%80%EC%9D%B4-jdk-17%EC%9D%84-%EB%8F%84%EC%9E%85%ED%95%9C-%EC%9D%B4%EC%9C%A0-ced2b754cd7)

### 1. JDK 8 사용하는 이유
- 발표된 LTS 버전 중 가장 오랜 SUPPORT 보장
- 기존 서비스와의 호환

### 2. ✔ JDK 17 도입 이유
- Java Support 기간 길음
- 신규 버전 위한 대비
- 다음 세대 플랫폼 호환 준비 (주된 이유) >> `spring boot 3.0` 부터 JDK 17이상 지원!!

---
### JDK 17 특징 😛
> [참고자료](https://youngwonhan-family.tistory.com/entry/Java-17-%EC%A3%BC%EC%9A%94-%ED%8A%B9%EC%A7%95-with-%EC%98%88%EC%A0%9C-%EC%83%98%ED%94%8C-%EC%BD%94%EB%93%9C)
#### `record`
- 불변객체 >> setter method 없음
- toString, equals, hashCode 자동 생성

#### `sealed ... permits`
- interface의 implement 하는 클래스 제한(`permit`) 가능

#### `Text Blocks`
- `"""` 


```java
String html = """
    <html>
        <body>
            <p>Hello, World!</p>
        </body>
    </html>
""";
```

#### `Pattern Matching`
- Object 객체의 타입을 switch에서 구분 가능
