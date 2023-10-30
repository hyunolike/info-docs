##  `jsconifg.js`
> [공색문서](https://code.visualstudio.com/docs/languages/jsconfig) <br/>
> [참고자료](https://velog.io/@kcj_dev96/jsconfig.json)
- `js` 관련 프로젝트라는 거 알려주는 용도
- `root` 위치 !!!
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/aae51124-7f8f-45c3-b07d-6c856d79d4c0)
### 옵션
- `exclude`
  - 프로젝트내에서 제외할 파일명
- `include`
  - 기본값 > 모든 파일 포함하도록 설정
  - 명시적으로 사용할때!!
- `compilerOptions` > ✔ 여기서 경로 설정도 가능
  - 여러가지 컴파일 옵션

 
```json
{
  "compilerOptions": {
    "module": "commonjs",
    "target": "es6",
     "baseUrl":".",
    "paths":{
    "@app/*": ["app/*"]
    }
  }
}
```

- 나머지는 알아서 봐 !! ㅡ,ㅡ


