 ## `리눅스` 무결성 확인 명령어 - `md5sum`
> [참고자료](https://bio-info.tistory.com/47)
### 사용 목적
- 파일 다운, 이동, 복사 > 원본파일과 동일한 파일인지 확인하는 목적
- `md5(Message-Digest algorithm 5)` + 해시 알고리즘 `sum(Check sum)` 값을 계산하는 명령어
### 사용 방법
```sh
md5sum [파일]

⭐파일 비교하고 싶다면
md5sum [파일1] [파일2] ...
```
### 비교
- 파일 이름이 달라도 데이트가 같다면 `md5sum` 값은 동일!
