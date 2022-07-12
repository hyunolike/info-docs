## `husky`로 githook!!
> [참고자료](https://library.gabia.com/contents/8492/)
- 깃 정책 강제 

### 1. Git Hooks
- git과 관련된 어떤 이벤트 발생 시, 특정 스크립트 실행할 수 있도록 하는 기능
- 크게 2가지로 나뉨!! ✔
  - 클라이언트 훅
  - 서버 훅
- 클라이언트 훅 ✔ 해당 페이지에서 다룰 훅!!! 
  - 커밋, 머지가 발생하거나 푸시가 발생하기 전 클라이언트에서 실행하는 훅
- 서버 훅
  - 깃 레포로 푸시가 발생했을 때 서버에서 실행하는 훅

### 2. 클라이언트 훅
- 종류
  - 커밋 워크플로 훅: `git commit` 명령으로 커밋 할 때 실행하는 훅
  - 이메일 워크플로 훅: `git am` 명령으로 이메일 통해 push 파일 적용할 때 실행하는 훅
  - 기타 훅...: `rebase` `merge` `push`와 같은 이벤트 실행할 때 실행하는 훅


|분류|훅|설명|
|-----|----|----------|
|커밋 워크플로 훅|`pre-commit`|`commit` 실행하기 전에 실행|
||`prepare-commit-msg`|`commit` 메시지 생성하고 편집기 실행하기 전에 실행|
||`commit-msg`|`commit` 메시지 완성 후 `commit` 을 최종 완료하기 전에 실행|
||`post-commit`|`commit` 완료 후 실행|
|이메일 워크플로 훅|`applypatch-msg`|`git am` 명령 실행 시 가장 먼저 실행|
||`pre-applypatch`|`patch` 적용 후 실행하며, `patch` 중단 시킬수 있음|
||`post-applypatch`|`git am` 명령에서 마지막으로 실행하며, `patch` 중단시킬 수 없음|
|기타 훅|`pre-rebase`|`rebase` 하기 전에 실행|
||`post-rewrite`|`git commit -amend` `git rebase` 와 같이 커밋을 변경하는 명령 실행 후 실행|
||`post-merge`|`merge` 끝나고 실행|
||`pre-push`|`git push` 명령 실행 시 동작하며 리모트 정보를 업데이트 하고 난 후 리모트로 데이터 전송하기 전에 실행. `push` 중단 가능|

### 3. Git Hooks 적용?
- `.git/hooks/pre-commit` >> ✔ 커밋 직전 실행 스크립트!!!
```shell
#!/bin/sh
echo 'Hello Gabia!'
exit 0 # Exit 코드가 0 이 아니면 커밋이 취소됨
```

### 4. master로 직접 push 방지
- Master로 직접 Push 하려고 하면 Push 중단시키는 훅 

```shell
#!/bin/sh
​
FORBIDDEN_HTTPS_URL="https://github.com/gabia/git-hooks-study.git" # insert your remote url (https)
FORBIDDEN_SSH_URL="git@github.com:gabia/git-hooks-study.git" # insert your remote url (ssh)
FORBIDDEN_REF="refs/heads/master" # insert branch ref
​
remote="$1"
url="$2"
​
if [ "$url" != "$FORBIDDEN_HTTPS_URL" -a "$url" != "$FORBIDDEN_SSH_URL" ]
then
    exit 0 # Forked Project 에서는 제한하지 않음
fi
​
if read local_ref local_sha remote_ref remote_sha
then
    if [ "$remote_ref" == "$FORBIDDEN_REF" ]
    then
        echo "DO NOT PUSH it master"
        exit 1 # 금지된 ref 로 push 를 실행하면 에러
    fi
fi
​
exit 0
```


- `.git/hooks/pre-push` 
- 아래 코드는 푸시 실행시 실행되는 코드 😁


```shell
#!/bin/sh
. "$(dirname "$0")/_/husky.sh"

cd frontend
# yarn test
```

### 5. ⭐`Git Hooks` 공유는 어떻게??
- `.git` 디렉토리는 버전관리 대상이 아님 >> Repository에 올라가지 않음
- 따라서, 깃 체계 하에서 `Git Hooks` 공유 불가 ㅠ,ㅠ
- Git Hooks 공유 방법 ✔
  1. `Git Hooks` 설정하는 스크립트 공유
  2. `Git Template` 활용
  3. `husky` 사용 😛 여기서 이걸 다루자


### 6. `husky`
- __Git Hooks__ 를 보다 쉽게 적용할 수 있는 `npm` 모듈
- husky 설치 `npm i -D husky`
