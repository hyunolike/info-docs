## npm install 옵션 정리
> [참고자료](https://c17an.netlify.app/blog/node.js/npm-install-%EC%A0%95%EB%A6%AC/article/)

### 1. npm install 및 패키지
- 동작 방식 2가지
  1. 패키지명을 명시해 특정 패키지 설치하는 동작
  2. 패키지명 명시하지 않고 `package.json` 파일의 의존성을 설치하는 동작
- ex. `npm install` 하면 `package.json`에 포함된 의존성 패키지들 일괄적으로 설치 진행 ✔

### 2. 특정 패키지 설치
- 2가지 옵션
  1. `dependencies` 목록에 추가될 `$ npm install (프로젝트명)` 
  2. 개발 단계에서만 필요한 `devDependencies` 목록에 추가될 `$ npm install -D (프로젝트명)`


|플래그|효과|
|-----|---------------------------------------|
|`-P`|패키지 설치하고 프로젝트의 `dependencies` 목록에 추가|
|`--save-prod`|패키지 설치하고 프로젝트의 `dependencies` 목록에 추가|
|`-D`|패키지 설치하고 프로젝트의 `devDependencies` 목록에 추가| 
|`--save-dev`|패키지 섪치하고 프로젝트의 `devDependencies` 목록에 추가|
|`-g`|패키지릂 프로젝트가 아닌 시스템의 `node_modules` 폴더에 설치|

#### 2.1 `-P` `--save-prod` 플래그 사용시
- 사용할일 많이 없음
- `-P` 기본 효과는 `$ npm install (프로젝트)` 와 완전 동일

#### 2.2 `-D` `--save-dev` 플래그 사용시
- `devDependencies` 에 추가
- 차이
  -  `dependencies`: express 패키지처럼 실제 코드에도 포함 >> 앱 구동을 위해 필요한 의존성 파일들
  -  `devDependencies`: concurrently 패키지처럼 실제 코드에 포함되지 않고 개발 단계에만 필요한 의존성 파일들

#### 2.3 `-g` `--global` 플래그 사용시
- `-g` `--global` 플래그 약간 다른 동작
- 윈도우 10 기준 >> `(사용자명)\AppData\Roaming\npm\node_modules`
  - node_modules 폴더 경로 >> `npm root -g` 통해 찾을 수 있음 
  - `-g` 플래그 사용시 `package.json` 의 의존성 목록 기재 안됨
### 3. 의존성 패키지 설치 시
- 일반 사용자 패키지 내려 받을 경우 `-production` 붙이면 `devDependencies` 제외한 의존성 파일만 내려받게 됨! ✔
