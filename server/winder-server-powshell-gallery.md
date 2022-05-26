## `PowerShell` 갤러리 - 윈도우 서버쪽 도커 설치를 위한 개념 정리 ✌
> [공식 자료](https://docs.microsoft.com/ko-kr/powershell/scripting/gallery/getting-started?view=powershell-7.2)
> [PowerShell Gallery 공식](https://www.powershellgallery.com/)

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
