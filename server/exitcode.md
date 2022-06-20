## 종료 상태 및 에러 메시지 처리
> [참고 자료](https://velog.io/@hidaehyunlee/minishell-4.-%EC%A2%85%EB%A3%8C%EC%83%81%ED%83%9C%EC%99%80-%EC%97%90%EB%9F%AC%EB%A9%94%EC%84%B8%EC%A7%80-%EC%B2%98%EB%A6%AC)
- ✔ 모든 명령어 >> `종료 상태(exit status)` 리턴
  - 성공 시 `0` 리턴
  - 실패 시 에러 코드로 해석될 수 있는 `non-zero(1~255)` 리턴

### 1. 종료 상태 코드
|종료 코드|뜻|에러 메시지|
|--------|----|---------|
|`0`|성공적으로 실행||
|`1`|광범위한 일반적 에러|- `Operation not permitted`<br>- `not a valid identifier`<br>- `too many arguments` 등등|
|`2`|쉘 builtin 명령어의 오사용|`No such file or directory` 등|
|`126`|__Permission__ 문제로 실행 불가능한 명령어의 구동|- `Permission denied`<br>- `Is a directory`|
|`127`|명령어 경로($PATH) 문제 혹은 명령어 오타|- `Command not found`<br>- `No Such file or directory`|
|`130`|치명적 에러 발생으로 인한 종료(Ctrl+C)|`Script terminated by Ctrl+C`|
|`255`|__exit__ 에 정수`(1~255)`가 아닌 인자 넘김|`numeric argument required`|
