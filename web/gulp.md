## Gulp
> [참고자료](https://velog.io/@leyuri/gulp%EB%9E%80) <br>
> [참고자료](https://velopert.com/1456)

- ![image](https://user-images.githubusercontent.com/61215550/217530664-10f14fe9-0393-41d7-9967-83540f89df0c.png)
- 빌드시스템: 반복 및 자주 사용되는 일은 자동화해주는 매우 유용한 툴!

### 개념
- 프론트엔드 자동화 빌드 툴
- 반복해서 하기 번거로운 작업들(파일 minification / sass 파일 컴파일 / Lint 등) 자동화 >> 개발 시간 단축시켜주는 역할
- 프론트엔드 개발을 하며 필요한 각종 기능들 플러그인으로 제공되어 확장성있는 작업 가능!

### 하는 일?
- 자바스크립트 라이브러리, 서드파티 앱등을 모으고 축소, 압축 실행
- 단위 테스트 수행
- LESS / CSS 컴파일링
- 브라우저 Refresh 도와줌!

### 😛 (추가) '클라이언트' 단에서 ES6 및 import 기능 사용 방법
> [참고자료](https://colinch4.github.io/2021-01-14/gulp/)
- ![image](https://user-images.githubusercontent.com/61215550/217531287-fe76561c-90e0-42a1-8cf6-1fb37fd702ee.png)
- `babel`: 단순히 클라이언트 사이드에서 ES6 문법 사용하게 해줌
    - `import` 기능 수행 x
- 🦁 ES6의 import 기능 추가하기 위해선! >> CommonJS 기반의 문법을 통해 모듈들을 관리 및 번들링 `webpack` 사용해야 됨!!  
