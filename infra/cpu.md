## ⭐️개발자도 알아야돼! `CPU` 아키텍처
> [참고자료](https://velog.io/@480/%EC%9D%B4%EC%A0%9C%EB%8A%94-%EA%B0%9C%EB%B0%9C%EC%9E%90%EB%8F%84-CPU-%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98%EB%A5%BC-%EA%B5%AC%EB%B6%84%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
### 1. CPU 클럭 단위 + 속도
- `Ghz` (기가헤르츠): 주파수의 진동 횟수
  - 수치 높을 수록 빠르다!
### 2. 대표적인 cpu 제조자
|제조사 명|설명|
|--|--|
|`Intel`|PC용 <br>안정적이다<br> `x86 아키텍처`|
|`AMD`|Intel의 `x86`호환 cpu 만드는 회사|
|`ARM`|`x86`과 전혀 다른 아키텍처 사용<br>과거, 가격 저렴하고 저전력 갖춰 **소형기기** 많이 사용<br>커스텀 가능<br>🍎 M1칩>>애플이 만든 `ARM 호환 cpu`|

### 3. 왜 알아야돼???
- `cpu` 아키텍처 종류: x86, amd64(x86_64), arm, arm64/v8
- 🔥 각 소프트웨어 실행 조건 > 컴파일 또는 동작 환경 갖춰줘야 함!
  - 대부분 라이브러리 >> 특정 CPU 아키텍처에 맞춰 컴파일 되어 있는 것을 갖다가 씀!
  - `Linux`: `*.so`(Shared Object)
  - `Window`: `*.dll`
- 예전 대부분 서버 >> 사전 컴파일해서 배포해도 별 문제가 안되었음!
- `ARM` 서버 등장으로 문제가 생김

### 4. 아키텍처 종류
- x86
  - Intel기반 32비트 cpu
  - 현존하는 프로그램 대부분 이 아키텍처 지원
  - windows, linux, mac os
- x86_64 (amd64)
  - Intel기반 64비트 cpu
  - x86 호환
  - amd 사에서 개발했지만 인텔과 크로스 라이센싱 !
  - windows, linux, mac os
- arm
  - arm 기반 32비트 cpu
  - x86과 아예 다름 전혀 호환 안됨
  - linux, mac os, andorid, ios 등 모든 `소형 기기`에서 성능 내야하는 경우(공유기)
- arm64 (arm64/v8)
  - arm 기반 64비트 cpu
  - 32비트 arm 호환
  - linux, mac os, android, ios ... 소현 기기 성능내야하는 경우
  - windows arm 버전 개발 중 (베타)
### 결론
- 프로그램 > 컴파일된 바이너리 (스크립트 언어 예외)
- 컴파일 > 어떤 cpu 헀는지에 따라 결과물 달라짐
