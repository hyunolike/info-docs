## `BASH` 쉘스크립트 문법
> [참고자료](https://inpa.tistory.com/entry/LINUX-%EC%89%98-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%ED%95%B5%EC%8B%AC-%EB%AC%B8%EB%B2%95-%EC%B4%9D%EC%A0%95%EB%A6%AC)
- 👨‍🌾 `Shell` `command line` 인터프리터 > 스크립트
  - 윈도우 버전 >> `batch(배치파일, .bat)`
  - 리눅스 버전 >> `shell script`

### 1. 첫번째 행 `Shebang`
- 첫번째 줄!! >> 어떤 쉘로 스크립트를 실행할지 정의하는 곳


```sh
#!/usr/bin/bash

echo $(which bash) # 디렉토리 위치 출력
```
#### 1-1. 유닉스 쉘 종류
|쉘|설명|
|:-:|:-:|
|`sh`|초기의 유닉스 쉘 (Bourne shell), 1977년 발표|
|`ksh`|콘 쉘, 1983년 데이비드 콘 개발, sh 확장하여 발표|
|`csh`|1978년, 버클리 대학 C언어 기반 쉘|
|`bash`|1987년 브라이언 폭스, sh과 대부분 호환|

### 2. 변수 선언
- 로컬변수, 전역변수, 환경변수, 예약변수, 매개변수 등 다양하게 존재
  - 변수 대,소문자 구별
  - 숫자 포함, 숫자로 시작 불가
  - 변수 모든값 `문자열` 저장
  - 자료형 기입 X
  - 값 사용 시 > 변수 명 앞 `$` >> echo ${data}
  - 값 대입 시 > 특수 문자 `$` 사용 x >> data=mac
  - 변수 생성시 `=` 앞 뒤 공백 없어야 됌
 
#### 2-1. 전역변수 & 지역변수
- 기본적으로 전역 변수
- 단, 함수 안 `지역변수` 사용 가능
  - `local` 키워드 사용!


```sh
# 기본적으로 전역 변수로 지정
string="hello world"

function string_test() {
    # local을 붙여야 지역변수로 인식. 만일 local을 빼면 전역변수 덮어쓰기가 되버림
    local string="hello local @@"
    echo ${string}
}

# 함수 호출
string_test # > hello local @@
echo ${string} # > hello world

# 변수 초기화
unset string
```
#### 2-2. 변수 타입 지정
- 문자열만 저장
  - 변수 자료형 타입 미리 지정하는 문법 가능
 

```sh
# -r 읽기 전용 타입 (상수 const라고 보면 된다)
declare -r var1
readonly var1

# -i 정수형 타입
declare -i number
number=3
echo "number = $number"     # number = 3

# -a 배열 타입
declare -a indices

# -A 연관배열(MAP) 타입
declare -A map

# -f 함수 타입
declare -f

# -x 환경변수(export) 지정
declare -x var3 # 스크립트 외부 환경에서도 이 변수를 쓸 수 있게 해준다.
```
#### 2-3. 환경변수
- `export` 키워드 사용
  - 주의. 예약변수와 변수명 겹치지 않게
- <img width="805" alt="image" src="https://github.com/hyunolike/info-docs/assets/61215550/27a4f8b3-4f7c-4041-84b4-b7fcfcf2d15b">
#### 2-4. 매개변수
- <img width="733" alt="image" src="https://github.com/hyunolike/info-docs/assets/61215550/62ce8f63-96d1-40cb-92d2-36a2a260598d">
#### 2-5. 예약변수
- 사용자 정의 불가 > 이미 정의된 변수
- <img width="823" alt="image" src="https://github.com/hyunolike/info-docs/assets/61215550/45cd347d-9b87-4f1b-b385-23e8ff681b0a">
#### 2-6. 이외의 변수 명령어


|명령어|설명|
|:-:|:-:|
|`set`|셸 변수를 출력하는 명령어|
|`env`|환경 변수 출력하는 명령어|
|`export`|특정 변수의 범위를 환경 변수의 데이터 공간으로 전송하여 자식 프로세스에서도 특정 변수를 사용 가능하게 해줌! 전역 변수의 개념|
|`unset`|선언된 변수 제거|
### 나머지는 직접 들어가서 확인하자 :)
