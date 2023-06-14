## npm 글로벌 패키지 확인 및 삭제
> [참고자료](https://dalya-tech.tistory.com/4)
```bash
글로벌 모듈 확인
$ npm list -g --depth=0

console
├── eslint@6.8.0
├── eslint-config-airbnb-base@14.0.0
├── eslint-plugin-import@2.19.1
├── eslint-plugin-prettier@3.1.2

...

글로벌 모듈 삭제
$ npm uninstall -g  <패키지이름>

console
removed 59 packages in 1.03s
```
