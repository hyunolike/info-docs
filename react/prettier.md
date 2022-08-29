## Prettier
> [참고자료](https://ux.stories.pe.kr/150)
- VSCode 크게 2가지
  -  `Prettier`: 코드 강제적으로 변경
  -  `Beautify`: 좀더 자유롭게 놔두는 편

### Prettier 익스텐션 설정
- `setting.json`

```json
{
  "workbench.colorTheme": "Default Dark+",
  "workbench.iconTheme": "material-icon-theme",
  "javascript.updateImportsOnFileMove.enabled": "always",
  "files.autoSave": "afterDelay",
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",

  // 추가 설정
  "prettier.printWidth": 80,
  "prettier.singleQuote": true,
  "prettier.arrowParens": "always"
}

```

### Prettier 설정
- 설정 적용 순서
  - `setting.json` < `.editorconfig` < `.prettierrc`


|설정|설명|
|----|------|
|`prettier.printWidth (default: 80)`|한줄 내에서 코드 맞춤 / 이 글자수 넘게 되면 줄바꿈! 코드 정리|
|`prettier.tabWidth (default: 2)`|텝 눌렀을 때 몇칸 띄어지는지 / 보통 4|
|`prettier.singleQuote (default: false)`|홑따옴표 쓸건지 설정 / 기본값 쌍따옴표|
|`prettier.trailingComma (default: 'none')`|객체, 배열, 함수 등의 후행에 쉼표 찍을지 제어|
|`prettier.bracketSpacing (default: true)`|객체 리터럴 내부의 공백 제어|
|`prettier.jsxBracketSameLine (default: false)`| jsx 요소의 마지막 다음 줄에 닫기 `>` 표시|
|`...이외에도 많아`|ㅎㅎㅎㅎㅎ|

