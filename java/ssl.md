## 자바 `ssl`인증서 등록하는 방법
> [참고자료](https://congabba.tistory.com/458)
- ⭐ 인증서 필요 이유 (아래 참고)
  - 외부 서버(ssl) > 내 서버(ssl 확인용 인증서 필요)
  - ![image](https://github.com/hyunolike/info-docs/assets/61215550/a5460539-00fc-4b60-a0a7-41fd1e6774c4)
### 준비
- 인증서: http://sslcert.cc/ 인증서 다운로드(무료)
- 로컬 자바 설정 > 환경변수
- `keytool` 동작 확인 > JDK 내장되어 있음

### ssl 인증서 등록 `keytool` 
```shell
# 인증서 저장
keytool -keystore ".\cacerts"(인증서 저장 위치) -importcert -file "D:인증서.crt"(가져올 인증서 위치)
# 비밀번호
changeit
# 저장 확인
keytool -list -keystore ".\cacerts" (인증서 저장 위치)
```
### 결과
![image](https://github.com/hyunolike/info-docs/assets/61215550/8466b273-6e9d-466f-8e00-b4d6db3e72fc)

### 구조
![image](https://github.com/hyunolike/info-docs/assets/61215550/32e09b3b-e3e1-4335-bd14-5825c6e82d51)

