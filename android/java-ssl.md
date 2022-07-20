## 자바 인증서
### 1. 인증서 개념 잡기
> [참고자료](https://wiki.kldp.org/HOWTO/html/SSL-Certificates-HOWTO/x70.html) <br>
> SSL 인증서: 신원을 확인하는 신분증, 배지!!! ⭐
- `SSL`: Netscape 사에서 웹서버와 브라우저 사이의 보안을 위해 만들어짐
  - Certificate Authority(CA) 불리는 서드 파티로부터 서버와 클라이언트 인증하는데 사용 ✔
- ![image](https://user-images.githubusercontent.com/61215550/179866103-f47b654d-39fd-4b3b-82ed-8a739ff151ce.png)

#### 1.1 동작 과정
![image](https://user-images.githubusercontent.com/61215550/179866782-c42ecb54-b71c-472c-94f4-d1cba8333fd8.png)

#### 1.2 용어 정리
- 인증서 정보 종류 
  - 인증서 소유자의 e-mail 주소
  - 소유자의 이름
  - 인증서의 용도
  - 인증서 유효기간
  - 발행 장소
  - Distinguished Name(DN): Common Name(CN) + 인증서 정보에 대해 서명한 사람의 디지털 ID
  - Public Key
  - 해쉬
- 서명 순서
  1. 해쉬 생성
  2. Private Key로 해쉬 암호화
  3. 암호화된 해쉬와 서명된 인증서를 메시지에 추가
  4. 받는 사람은 따로 해쉬 생성
  5. 받은 메시지에 포함된 해쉬를 Public Key 이용해 복호화
  6.  4,5번 과정에서 생성된 해쉬 비교

|용어|설명|
|-----|------|
|개인키/공개키<br>`Private Key/Public Key`|- 키쌍은 소수, 그 길이는(bit 단위) 암호화의 강도|
|인증서 `Certificate`|- 당신과 접속해있는 웹 사이트 신뢰 여부 판단??|
|대칭키|...|
|암호화 알고리즘|...|
|해쉬|- 해쉬 함수에 의해 만들어지는 숫자/함수는 단방향 연산 함수<BR>- 해쉬의 용도 >> 원본 메시지 손상 되었는지 알아내는데 목적/해쉬값 변경시키지 않고 원본을 조작하는 것은 극히 어려움 >> 메시지 손상을 방지하기 위해 널리 사용 |
|서명 `Signing`|- 특정 메시지를 내가 작성했다는 것을 인증하는 역할|
|암호문|- 기존 패스워드 확장한 시스템<br>- 단순히 암호의 한계가 더 길어졌다는 것 뜻함/최근 Unix 시스템은 MD5 사용하고 있기에 암호의 길이 제한 없어짐|
  
### 2. SSL 인증서 자바 CA인증서에 추가하는 방법
> [참고자료](https://cert.crosscert.com/ssl%EC%9D%B8%EC%A6%9D%EC%84%9C-java-ca%EC%9D%B8%EC%A6%9D%EC%84%9C%EC%97%90-%EB%A3%A8%ED%8A%B8-%EC%9D%B8%EC%A6%9D%EC%84%9C-%EC%B6%94%EA%B0%80%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95/) <br>
> ⭐ 윈도우에서는 `cmd` 창으로 실행!! `powershell` 명령어 안먹히는 부분 있음 ㅠ,ㅠ - [참고자료](https://www.lesstif.com/java/java-keytool-keystore-20775436.html)
- 인증 방법 요약
  - 서버: 클라이언트에 인증서 전달
  - 클라이언트: 서버로부터 전달받은 인증서 루트인증서저장소(cacerts)에 있는 루트인증서로 신뢰성 검증
  - 📌주의: 이때 클라이언트의 루트인증서(cacerts)에 서버로부터 전달받은 인증서를 검증할 루트인증서 없다면  신뢰성 검증 못해 통신 불가 ㅠ,ㅠ
- 방법
  - 😛 사전 작업: 클라이언트의 루트인증저장소(cacerts)에 서버의 인증서를 발급한 인증기관의 루트인증서를 등록 / 해당 루트인증서를 다운받거나 전달받은 후 아래의 명령어 등록
  - `keytool -importcert -alias 등록한 명칭 -keystore JAVA_HOME/PATH/cacerts-files 루트인증서`
  - cecerts에 설정된 비밀번호: `changeit`
  
### 3. 결과 확인 - 샌드버드
![image](https://user-images.githubusercontent.com/61215550/179869288-f38c83d8-acc4-418b-a7ae-76e30d10da47.png)
