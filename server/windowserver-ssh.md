## 윈도우 서버 `SSH Server` 설정
> [참고 자료](https://cloudeveloper.net/windows-10-%EB%84%A4%EC%9D%B4%ED%8B%B0%EB%B8%8C-%EB%B0%A9%EC%8B%9D%EC%9C%BC%EB%A1%9C-ssh-%EC%84%9C%EB%B2%84-%EC%84%A4%EC%A0%95%ED%95%98%EA%B8%B0-64988d87349)

### 설치 순서
1. `OpenSSH` 설치
  - 윈도우 서버 2019이후 버전은 __윈도우 설정__ 에서 설치 가능
  - 나머지는 파일 다운로드 받아 설치
2. 비대칭 키 인증 적용 ✔
  - 비밀번호 대입을 통한 공격 방지(Public Key 인증 방식 사용 / 비밀 번호 인증 방식 비활성화) >> `ssh_config` 파일 수정(아래 참고)
 
```
PubkeyAuthentication yes
PasswordAuthentication no
PermitEmptyPasswords no
```
- 주석 해제하고 위와 같이 수정

3. SSH 공개 키 관리 방식 선택
- `$HOME\.ssh\authorized_keys` 방식 ✌
  1. `ssh_config` 파일 수정(아래 코드 참고)
  2. 로그인 하려는 홈 디렉터리 이동해 `.ssh` 폴더 생성
  3. `authorized_keys` 파일 생성 후 `SSH` 공개 키 가져와 기록하고 
  4. 마지막으로 아래에 설명할 __인증 키 정보 담은 파일 권한 설정__ 반드시 설정해야 됨⭐(중요해)
  

```
Match Group administrators
  AuthorizedKeysFile
  __PROGRAMDATA__/ssh/administrators_authorized_keys
```
- 주석 처리 해야됨!!! ✔
- `administrators_authorized_keys` 방식 ✌ >> 매번 새롭게 등록하지 않고, 한 곳에서 파일 관리 가능!!(기본적으로 이 방식 사용)
  1. 해당 파일은 기본적으로 생성되지 않으므로 `administrators_authorized_keys` 파일 생성(파일 확장자 없어야됨)
  2. 마지막으로 아래에 설명할 __인증 키 정보 담은 파일 권한 설정__ 반드시 설정해야 됨⭐(중요해)

4. 인증 키 정보를 담은 파일 권한 설정 >> 난이도 어려움
  - 시스템 계정만 접근할 수 있도록 변경

```shell
$authorizedKeyFilePath = "..."
icacls.exe $authorizedKeyFilePath /remove “NT AUTHORITY\Authenticated Users”
icacls.exe $authorizedKeyFilePath /inheritance:r
Get-Acl “$env:ProgramData\ssh\ssh_host_dsa_key” | Set-Acl $authorizedKeyFilePath
```

... 나머지 내용은 위 링크 참고
