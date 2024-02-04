## `subtree` Github Repo 하나로 합치자
> [참고자료](https://olrlobt.tistory.com/47)
- 여러가지 레포를 1개의 레포로 합치자
  - 커밋 이력까지~~~
 
### Git subtree
- 여러 개의 Git repository를 폴더 하나 큰거에서 관리할 수 있게하는 기능
- 👨‍🌾 subtree > `history` 그대로 유지! > commit 내역 + github의 잔디 보호ㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋ


|`submodule`|`subtree`|
|:-:|:-:|
|하나를 쪼개는 기능|하나로 만드는 기능|
### subtree 명령어 종류
- `git subtree add`: 다른 깃 레포 > 하위 디렉터리 추가
- `git subtree pull`: 다른 깃 레포 . 변경사항 가져와 > 하위 디렉토리 병합
- `git subtree push`: 하위 디렉터리 . 변경사항 > 다른 레포 푸시
- `git subtree split`: 하위 데릭터리 . 변경사항 > 다른 레포 분할

### 고고고 해보자
```bash
git subtree add --prefix=[child repository name] [child git URL] [Branch]

👨‍🌾 --prefix : 이름 그대로 사용하기 위해!
```
