## SSH 명령어
> [참고 자료](https://wlsvud84.tistory.com/12)

### SSH 접속(원격지 접속) 
- `ssh [사용자 계정]@[원격지 ip]`

### 옵션
- ![image](https://user-images.githubusercontent.com/61215550/172792072-f006d55f-85fa-4af4-b700-d9de62e9ef27.png)


### 추가 - `ssh-keygen`
> [참고 자료](https://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_ssh-keygen)
- ssh 키 생성 명령
- `ssh-keygen [option]`

|옵션|설명|비고|
|----|-----|-----|
|`-b bits`|생성할 키 비트수 지정 <br>최소 768비트 필요 / 디폴트값 2048비트 설정||
|`-C comment`|주석 입력 가능 / 서버에 따라 특별한 용도 사용||
|`-t`|암호화 방식 설정|`$ssh-keygen -t rsa` >> rsa암호화 방식으로 키 생성|
|`-f`|저장할 파일명 지정. 경로 지정||
