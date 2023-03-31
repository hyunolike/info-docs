## git stash
> [참고자료](https://git-scm.com/book/ko/v2/Git-%EB%8F%84%EA%B5%AC-Stashing%EA%B3%BC-Cleaning)
- ⭐완료되지 않은 작업 `stash stack` 에 임시저장 가능
- 파일의 변경 내용을 일시적으로 기록해두는 영역 - [참고자료](https://mine-it-record.tistory.com/651)
- `git stash` == `git stash push`
- 💡 우선순위가 높은 작업들을 모두 처리한 후 `git stash` 로 임시 저장한 내용들을 다시 불러와 작업 이어할 수 있음


### 명령어
```shell
git stash push -m --keep-index // 이미 Staging Area에 들어 있는 파일을 Stash 하지 않음

git stash -u 
// -u 옵션: -include-untracked의 줄임말
// 언트래킹 파일들도 stashing area에 추가하고 싶을 때 사용
```

### 실무 적용
- 개발 브랜치에서 메인 브랜치로 푸시하지 않을 코드 스테이징하는 상황
  - 다시 개발 브랜치로 풀을 받아 깃 스태시로 임시 저장된 개발 코드 다시 적용하는 방식
- ![image](https://user-images.githubusercontent.com/61215550/228993025-d1914fa3-2e4b-4bd1-a85c-5f9d17790376.png)
