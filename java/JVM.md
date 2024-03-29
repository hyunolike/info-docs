## JVM `Stack` `Heap`
- 자바 바이트코드 > 타겟 플랫폼 상관 없이 > JVM 위에서 동작
  - JVM > 타겟 플랫폼 의존 👀
  - <img width="656" alt="image" src="https://github.com/hyunolike/info-docs/assets/61215550/0bb3962d-110b-4409-91cd-ca72881df452">
### 굳이 JVM ???
- 기존 `C` `C++` > 크로스 컴파일해서 배포하고 있음
- ⭐️ 자바 > 네트워크 연결된 모든 디바이스 작동하는 것 목적!!!
  - 디바이스 마다 > 운영체제 / 하드웨어 다름 > 플랫폼 의존하지 않도록 언어 설계 > 👨‍🌾 Java Bytecode, JVM

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
### 구조
> 배치 --> 실행
- ![image](https://user-images.githubusercontent.com/61215550/234150117-37a04056-f7f7-403e-8c12-c86a02d49cdf.png)
#### 1. 클래스 로더
- 로드된 바이트 코드 `.class` 엮어서 JVM의 메모리 영역인 Runtime Data Areas에 `배치`
#### 2. 실행 엔진
- 클래스 로더를 통해 런타임 데이터 영역에 배치된 바이트 코드를 명령어 단위로 읽어서 `실행`
#### 3. 런타임 데이터 영역
- 자바 애플리케이션 실행할 때 사용되는 데이터 `적재`하는 영역
