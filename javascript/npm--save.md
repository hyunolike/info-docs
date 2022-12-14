## npm `--save` 옵션
> [참고자료](https://xtring-dev.tistory.com/11)
- ✔ `npm5` 부터는 `--save` 사용하지 않아도 dependencies 항목 추가 (기본으로 사용되는 기능으로 생략 가능!)
- `npm(Node Package Manager)`: 프로젝트에 필요한 라이브러리를 다운로드 또는 관리 할 수 있도록 해주는 프로그램

### `--save` 붙이는 이유
- `--save` 옵션 >>  `package.json` 의 `dependency` 항목에 모듈 추가한다는 의미
- 이전 npm 버전에서는 `node_modules` 제거 시 >> `--save` 하지 않은 라이브러리 다시 추가하지 않음 ㅠ,ㅠ 
- ⭐ `npm5` 부터는 `--save` 옵션 기본으로 적용!!

### 옵션 설명
|옵션|설명|
|--|---|
|`-P` `--save-prod`|package.json의 `dependencies` 패키지 등록 (default)|
|`-D` `--save-dev`|package.json의 `devDependencies` 패키지 등록|
|`-O` `--save-optional`|package.json의 `optionalDependencies` 패키지 등록|
|`--no-save`|dependenciese 패키지 등록 안함|
