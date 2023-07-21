## java - `keytool` SSL 인증서
> [참고자료](https://www.lesstif.com/java/java-keytool-keystore-20775436.html)
- `KeyStore` 인터페이스
    - `Encryption` `Decryption` 및 `Digital Signature` 사용 > Private key, Public key & Certificate 추상화 제공
- 인증서 패치 가능
- 인증서 Import
- Private Key import
- alias 변경
### Keytool
- `Keystore`기반 인증서 / 키 관리
- 커멘드 방식의 유틸리티
    - 커멘드 방식의 OpenSSL과 비슷한 용도로 사용가능한 프로그램\
 
#### ✔ KeyStore Type
- `-keystore` 옵션 > 키스토어 파일의 경로 지정 x > 사용자의 홈디렉토리 `.keysotre 파일 찾음
- `JKS` (Java KeyStore) 타입 처리

### 준비사항
- 자바 버전 환경변수 설정
- 해당 버전 이용해 키툴 사용
