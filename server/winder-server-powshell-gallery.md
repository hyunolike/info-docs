## `PowerShell` 갤러리 - 윈도우 서버쪽 도커 설치를 위한 개념 정리 ✌
> [공식 자료](https://docs.microsoft.com/ko-kr/powershell/scripting/gallery/getting-started?view=powershell-7.2)
> [PowerShell Gallery 공식](https://www.powershellgallery.com/) 📌
> [PowerShell 공식 문서](https://docs.microsoft.com/en-us/powershell/?view=powershell-7.2) 📌

![image](https://user-images.githubusercontent.com/61215550/170388063-ee1e6cbc-1e0f-458a-924c-4f7480c4d9d5.png)

- 다운로드하고 이용가능한 스크립트
- 모듈 및 DSC 리소스 포함하는 패키지 리포지토리 ✔ > ⭐PowerShell 모듈, 스크립트 및 DSC 리소스의 중앙 리포지토리
- 매개 변수 사용해 결과 필터링 가능
  - 이름
  - AllVersions
  - MinimumVersion
  - RequiredVersion
  - 태그
  - Includes
  - DscResource
  - RoleCapability
  - 명령
  - 필터
### 윈도우에 PowerShellGet 설치
- 윈도우랑 같이 제공 ✔

### 1. 패키지 확인
- `Find-Module -Name PSReadLine -Repository PSGallery|Get-Member`
  - PSReadLine 모듈에 대한 데이터 반환

### 2. 패키지 다운로드
- `Install-Module` 기본적으로 `$env:ProgramFiles\WindowsPowerShell\Modules` 에 모듈 설치 >> __관리자 계정 필요__ ✔
  - `Scope CurrentUser` 매개 변수 추가 시 >> ` $env:USERPROFILE\Documents\WindowsPowerShell\Modules` >> 일반 사용자 계정
- `Install-Module` `Install-Script` >> 최신 버전의 패키지 설치
  - 이전 버전 설치하고 싶으면 >> `-RequiredVersion`

### 3. 패키지 업데이트
- `Update-Module` `Update-Script` 
  - 선택적 업데이트 시 >> `-Name` 매개변수 추가 

### 4. 설치된 패키지 나열
- `Get-InstalledModule` 

---
### 추가 매개변수 정리
|용어|설명|
|----|-----|
|`-WhatIf`|변화 일으키는 모든 것에 사용|
|`-Force`|기존 항목 강제 덮어쓰기 / 읽기 전용 파일 시스템 속성 무시|
|`-Confirm`|위와 동일 <br> 작업 실패 시 `-Force`랑 동일 / 예. 파일 쓰기 작업 확인할수 있지만 파일이 읽기 전용 속성으로 보호 가능|
