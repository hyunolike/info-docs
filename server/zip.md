## zip
> Windows Server <br>
> [참고 자료](https://lee-mandu.tistory.com/530)
- 기본 명령어 아님. ✔
- [zip 프로그램 다운로드 사이트](http://stahlworks.com/dev/?tool=zipunzip)

### 설정
- `C:\windows\system32` 파일 위치

### 1. `unzip`
> [참고 자료](https://websetnet.net/ko/unzip-a-file-in-linux-terminal-using-unzip-command-with-examples/)
- 옵션이 없는 기본 동작 >> 지정된 zip 아카이브에서 모든 파일을 현재 디렉토리로 추출
- `unzip [option] zip_file`
#### 1.1 디렉토리 압축 풀기
- `unzip -d target_directory zip_file`

#### 1.2 현재 디렉토리에 추출
- `unzip -j zip_file`

#### 1.3 파일 덮어쓰기
- `unzip -o -d target_directory zip_file`

#### 1.4 파일 덮어쓰지 않기
- `unzip -n -d target_directory zip_file` 

#### 1.5 기타 옵션
|옵션|설명|
|-----|-----|
|`-a`|압축 해제 텍스트 파일을 기본적으로 자동 변환|
|`-L`|파일 이름을 대문자 시스템에서 소문자로 변환|
|`-C`|대소 문자를 구분하지 않고 이름을 일치|
|`-q`|더 조용히ㅋㅋㅋㅋ|
|`-o`|항상 덮어쓰기|
|`-n`|파일을 추출 할 때 파일 덮어쓰지 않기|
