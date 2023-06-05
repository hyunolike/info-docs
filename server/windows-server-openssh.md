## Windows Server 2016 - OpenSSH 설정
> [참고자료](https://cloudeveloper.net/windows-10-%EB%84%A4%EC%9D%B4%ED%8B%B0%EB%B8%8C-%EB%B0%A9%EC%8B%9D%EC%9C%BC%EB%A1%9C-ssh-%EC%84%9C%EB%B2%84-%EC%84%A4%EC%A0%95%ED%95%98%EA%B8%B0-64988d87349)
- 기본 제공 버전 >> Windows 10 & Windows Server 1709

### 비대칭 키 인증 적용
- `$env:PROGRAMDATA\ssh\sshd_config`
- 아래 주석 처리 😛
  


```
PubkeyAuthentication yes
PasswordAuthentication no
PermitEmptyPasswords no
```
### ⭐ SSH 공개 키 관리 방식
#### 1. $HOME\.ssh\authorized_keys 파일을 사용하는 방법
- 아래 코드 주석처리 필요



```
Match Group administrators
  AuthorizedKeysFile
  __PROGRAMDATA__/ssh/administrators_authorized_keys
```
##### 1.1 각 사용자 홈 디렉토리 이동 후 `.ssh` 디렉터리 생성 
- `authorized_keys` 파일 추가 (확장자 없어야됨) >> SSH 공개 키 값 넣기!
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/717615a4-6381-40f3-b41d-f53db74ea142)


#### 2. administrators_authorized_keys를 사용하는 방법
- `Windows Server 2019(1809) 기본 포함 (OpenSSH)
- 관리자가 아닌 사용자들을 제외하면 모든 공개 키 
  - `$env:PROGRAMDATA\ssh\administrators_authorized_keys`에 저장되어 서로 공유
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/e902d6ee-9dec-492f-b3eb-4fd8cb9e2477)


