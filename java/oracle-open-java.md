## Oracle vs Open 자바 차이
> [참고자료](https://broccolies.com/2021/04/22/oracle-jdk%EC%99%80-open-jdk%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90-%EB%B9%84%EA%B5%90/)

- JDK(Java Development Kit): 자바 플랫폼 프로그래밍에서 사용되는 소프트웨어 환경 / 😛여기에는 뭐가 ?? `JRE(개별 런타임)` 포함되어 있다!!

### 주요 차이점
|차이점|오라클|오픈|
|-----|-----|----|
|배포일정 `Release`|3년마다 릴리즈|6개월마다 릴리즈|
|라이센스|2019년 1월이후 출시된 Oracle Java SE 8의 공개 업데이트부터 상용 라이센스 없이 비즈니스, 상업용 또는 생산 사용 불가 ㅠ,ㅠ|`GNU GPL` 버전 2이므로 완전한 오픈 소스이며 자유롭게 사용 가능!!|
|성능 - 동일한 기반으로 실질적인 기술차이 ❌|성능 >> 응답성 및 JVM성능면에서 더 좋음|자주 릴리즈 >> 불안정성 요소 가능|
|기능 및 옵션|`Flight Recorder` `Java Mission Control` `Application Class-Data Sharing` + 가비지 수집 옵션, 더 나은 렌더러|`Font Rendering` + 지속적 릴리즈로 개선 중 ㅠ,ㅠ|

### 오픈 JDK 
```
AdoptOpenJDK
Amazon Corretto
Azul Zulu
Bck2Brwsr
CACAO
Codename One
DoppioJVM
Eclipse OpenJ9
GraalVM CE
HaikuVM
HotSpot
Jamiga
JamVM
Jelatine JVM
Jikes RVM (Jikes Research Virtual Machine)
JVM.go
leJOS
Maxine
Multi-OS Engine
RopeVM
uJVM
```
