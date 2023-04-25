## JVM
> [참고자료](https://inpa.tistory.com/entry/JAVA-%E2%98%95-JVM-%EB%82%B4%EB%B6%80-%EA%B5%AC%EC%A1%B0-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%98%81%EC%97%AD-%EC%8B%AC%ED%99%94%ED%8E%B8#native_method_library)
- ![image](https://user-images.githubusercontent.com/61215550/234148959-7217e518-b0df-494d-b254-1956c18c2d67.png)
- ⭐ 컴파일된 `.class` 파일을 어떠한 처리를 거쳐 프로그램을 실행하는 과정
### 자바 가상 머신 동작 방식
- `클래스 로더` 통해 읽어 `자바 api`와 함께 실행하는 것
- ![image](https://user-images.githubusercontent.com/61215550/234149229-15cae6c6-db00-45fe-9537-972e4d34ddb2.png)
  1. 자바 프로그램 실행 >> JVM >> OS로부터 메모리 할당
  2. 자바 컴파일러 `javac` >> 자바 소스코드 `.java` >> 자바 바이트 코드 `.class` 컴파일
  3. `class Loader` 동적 로딩 통해 필요한 클래스들 로딩 및 링크 >> Runtime Data Area(실질적인 메모리 할당 받아 관리하는 영역) 올ㄹ림
  4. `Runtime Data Area` >> 로딩된 바이트 코드 >> Execution Engine 통해 `해석`
  5. ✔ Execution Engine에 의해 Garbage Collector의 작동와 Thread 동기화 이뤄짐

