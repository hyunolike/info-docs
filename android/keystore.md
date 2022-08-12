## 안드로이드 키스토어 사용해 데이터 암복호화
- 여기서 말하는 키스토어는 APK 추출 시 필요한 jsk 키 아님! 
- `java,security,KeyStore` 내장 라이브러리 ✅

### 1. 왜 사용?
- 서버 db에 저장하기에는 가끔 쓰이는 것도 아니고 / 규모가 큰 것도 아니고 / 자주 변경되는 것도 아니고 / 앱 내 자주사용하는 데이터
- `Shared Preferences` 
  - 앱 내장 디렉토리에 xml파일 생성 
  - `Key: value` 값 저장하는 방식
- 규모가 크지 않고, 앱 삭제 시 함께 삭제되니까 일석이조✌️
- 하지만 ㅠ,ㅠ >> 루트 권한으로 앱 실행 시 >> 앱 내부 파일 확인 및 수정 가능 >> 이를 위해 **데이터 암호화** 필요

### 2. 데이터 암호화?? 
- 방법
  - 암호화 알고리즘(base64)
  - Android KeyStroe 시스템 ⭐️

### 3. Android KeyStore???
- 안드로이드 컨테이너 부분 >> 개인 키 저장 >> 암복화 시 해당 키 가져와 진행
- 컨테이너 저장한 순간, 해당 키를 사용자가 직접 추출 및 확인 불가
- 애플리케이션 단에서 직접 컨테이너 접근 어려움 / 시스템 측에서만 접근 가능 / 보안성 높아짐
- 앱 삭제 시 키도 같이 삭제 / 개개인의 앱 별로 키가 다르기에 고유한 공통키 알고리즘 따로 없음
- 패키지 덮어씌우거나 APK까지 접근하는 모든 방법 또한 통하지 않음
- `Android M(API 23) 이상` 부터 가능
#### 3.1 보안적 특징
> [참고자료](https://blog.yatopark.net/2016/05/01/%EC%95%88%EB%93%9C%EB%A1%9C%EC%9D%B4%EB%93%9C-keystore-%EC%8B%9C%EC%8A%A4%ED%85%9C/)
- 키 추출 방지
- 키 사용에 대한 인증처리
  - 암호화
  - 인증 유효기간
  - 사용자 인증
#### 3.2 추가 로직 자료
|로직 자료|
|:-----:|
|![image](https://user-images.githubusercontent.com/61215550/184282308-d255dcd8-f253-4b37-bb42-7756286d0ab2.png)|
|![image](https://user-images.githubusercontent.com/61215550/184282280-eabc6b20-2d76-49ad-a6a1-1aa88e2992d0.png)|




### 4. (추가) Shared Preferences 
- Android에서 제공하는 xml 저장위한 기술
- xml 파일 write/read 통해 저장된 정보 빠르게 읽고 쓰기 가능
- `/data/data/패키지명/shared_prefs/SharedPreferences` 저장
- 보안을 위해 >> `Android Keystore` 이용해 암호화
- ![image](https://user-images.githubusercontent.com/61215550/184280542-e7954449-fd72-471b-90a0-7800e6f201d0.png)
- 암호화🤪
  1. 컨테이너에서 암호키 로드
  2. 메모리에 있는 민감정보&암호키 >> 암호 알고리즘 >> 암호문 생성
  3. 만든 암호문 xml에 안전하게 저장
- 복호화😜
  1. 컨테이너에서 암호키 꺼냄
  2. xml에 저장된 암호문 꺼냄
  3. 암호문과 암호키를 복호 알고리즘 통해 복호화하여 원래 평문으로 만듬

