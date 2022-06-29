## 암호화 알고리즘
> [참고 자료](https://alexonepath.github.io/category/etc/etc-crypto.html)
- ![image](https://user-images.githubusercontent.com/61215550/176381929-8f7a0743-de4f-41d1-86bd-b72bcb3bd0a1.png)

### 1. 정의
|용어|설명|
|----------|------------|
|평문 `Plaintext`|해독 가능한 형태의 메시지(암호화 전 메시지)|
|암호문 `Cipertext`|해독 불가능한 형태의 메시지(암호화된 메시지)|
|암호화 `Encryption`|평문 --> 암호문으로 변환하는 과정|
|복호화 `Decryption`|암호문 --> 평문으로 변환하는 과정|
|전자서명|- __송신자__ 의 Private Key로 메시지를 서명하여 전달<br>- __수신측__ 에서는 송신자의 Public Key를 이용해 서명값 검증|
|양방향 암호화|암호화와 복호화 과정을 통해 송수신간 주고받는 메시지를 안전하게 암,복호화 하는 과정|
|단방향 암호화|해싱(`Hashing`)을 이용한 암호화 방식으로 양방향과는 다른 개념 / 평문을 암호문으로 암호화 가능하지만 암호문을 평문으로 복호화 불가|

### 2. 대칭키 & 비대칭키(공개키) 암호화
- 대칭키 암호화
  - __같은 키__ 이용하여 메시지 암,복호화 하는 것
- 비대칭키 암호화
  - 메시지 암호화 하는 키와 복호화 하는 키가 다름
- 추가 설명⭐
  -  암호화 알고리즘에 따라 다르게 사용!! ✔
  -  전자서명을 위한 알고리즘 >> Private Key로 메시지 서명하고 Public Key로 검증 진행
  -  메시지 교환 >> Public Key로 메시지 암호화하고 Private Key로 복호화 
- 두가지 방식의 조합
  - 비대칭키는 대칭키에 비해 느리다는 단점 존재 아래와 같이 활용
  - 대칭형 암호키를 비대칭형 암호화로 암호화하여 수신측에 전달
  - 이후 평문에 대한 암복화를 대칭형 암호화를 이용하여 수행

|메시지 교환 알고리즘|설명|비고|
|--------------------|---------------------------|--------------|
|대칭키 암호화|`AES128` `AES256` `SEED(국내표준)` <BR> 암,복호화 키가 같음. 문제점은 수신측에 키를 전달하는 과정에서 유출우려 존재||
|비대칭키 암호화|`DSA(전자서명)` `RSA(메시지 암,복호화)` <BR> - 대칭키에 비해서 느리다는 단점 <BR> - 키 생성 시 Private Key, Public Key 2개의 키 도출, Public Key 공개 되도 문제 없음 <br> `ECC(Elliptic Curve Cryptography)`||
  
#### 2.1 `ECC` - 비대칭키 암호화
- 타원곡선 암호로써 RSA에 비해 짧은 길이의 키를 사용하면서도 비슷한 수준의 안전성 제공
- 비트코인 및 이더리움에서도 사용
- `ECC` 기반의 암호화
  - `ECDSA(Elliptic Curve Digital Signature Algorithm)`: 전자서명(ECC 암호화 알고리즘을 전자서명에 사용한 것)
  - `ECDH(Elliptic Curve Diff-Hellman)`: 키 교환 알고리즘(자신의 Private Key와 상대방의 Public Key를 사용해 공통된 `Secret` 키 도출)
  - `ECIES(Elliptic Curve Integrated Encryption scheme)`: 통합 암호화 방식(Public Key로 암호화하고 Private 복호화)
  
