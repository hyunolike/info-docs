## 디지털 서명
> [위키백과](https://ko.wikipedia.org/wiki/%EB%94%94%EC%A7%80%ED%84%B8_%EC%84%9C%EB%AA%85) <BR>
> [참고 자료](https://academy.binance.com/ko/articles/what-is-a-digital-signature)
 
- 네트워크에서 송신자의 신원을 증명하는 방법
- 디지털 데이터의 진위성과 무결성을 검증하는데 사용되는 암호 메커니즘
- 보통 3개의 알고리즘으로 구성
  1. 공개키 쌍을 생성하는 키 생성 알고리즘
  2. 이용자의 개인 키를 사용하여 서명(전자서명)을 생성하는 알고리즘
  3. 그것과 이용자의 공개키를 사용해 서명 검증하는 알고리즘
- 디지털 서명 중요한 이유 ✔
  - 데이터 무결성
  - 진위성
  - 부인 방지

### 1. 해시 함수
- 해싱: 디지털 서명 시스템의 핵심 요소
  - 어떠한 크기의 데이터라도 고정된 크기의 값으로 변환하는 과정 포함
  - 해시값(메시지 다이제스트): 해시 함수에 의해 생성된 결괏값

### 2. 공개 키 암호 방식(PKC)
- 하나의 공개 키 + 하나의 개인 키
- 대칭형 암호화보다 안전

### 3. 디지털 서명 과정 ⭐
- 해싱, 서명, 검증 
#### 3.1 데이터 해싱
#### 3.2 서명
- 정보가 해시된 다음, 메시지 발신자의 서명 필요
#### 3.3 검증
