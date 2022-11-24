## 심볼릭 링크
> [참고자료](https://madplay.github.io/post/what-is-a-symbolic-link-in-linux)
- 특정 파일 / 디렉터리에 대한 참조를 포함하는 특별한 파일
- ✔ windows 운영체제의 `바로 가기` 와 같은 기능

### 사용법
#### 1. 심볼릭 링크 생성
```shell
$ ln -s [대상 경로] [링크 경로]
```

#### 2. 심볼릭 링크 삭제
```shell
# 테스트할 `test` 디렉터리 생성
$ mkdir test

# 테스트 디렉터리에 대한 `link_sym` 심볼릭 링크 생성 
$ ln -s test link_sym

# 삭제 명령어 수행
$ rm link_sym/
rm: cannot remove `link_sym/': 디렉터리입니다

# `/`를 제거하고 삭제 명령어 수행
$ rm link_sym
```

##### ⭐삭제 시 주의점
```shell
# 테스트할 `test` 디렉터리 생성
$ mkdir test

# `test` 디렉터리 하위에 `test.txt` 파일 생성
$ echo "hi" > test/test.txt

# 테스트 디렉터리에 대한 `link_sym` 심볼릭 링크 생성 
$ ln -s test link_sym

# 삭제 명령어 수행
$ rm -r link_sym/
rm: cannot remove `link_sym': 디렉터리가 아닙니다

# `test` 디렉터리는 삭제되지 않았으나, 내부의 파일은 삭제됨
```

#### 3. 하드링크
- `ln` 명령어 사용 시 `-s` 옵션 사용하지 않는 경우 **하드 링크** 생성
  - 하드 링크의 경우 원본과 동일한 `inode` 가짐 >> 원본 파일 삭제되더라도 사용 가능!
