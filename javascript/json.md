## JSON & Method
> [참고 자료](https://ko.javascript.info/json)
- JSON 본래 자바스크립트에서 사용할 목적으로 만들어진 포맷
  - 라이브러리 사용 >> 다른 언어에서도 사용가능한 경우가 많아짐
- `JSON.stringify`: 객체 --> JSON
- `JSON.parse`: JSON --> 객체
### `JSON.stringify`
- 객체 뿐 아니라 원시 값도 적용 가능
  - 배열
  - 원시형: 문자형, 숫자형, 불린형 값, NULL
- 무시되는 프로퍼티
  - 함수 프로퍼티(메서드)
  - 심볼형 프로퍼티(키가 심볼인 프로퍼티)
  - 값이 `undefined` 인 프로퍼티
- ✔ `replacer`로 원하는 프로퍼티만 직렬화
  - `let json = JSON.stringify(value[, replacer, space])`
  - value: 인코딩 하려는 값
  - replacer: JSON으로 인코딩 하길 원하는 프로퍼티가 담긴 배열. 또는 매핑 함수 `function(key, value)`
  - space: 서식 변경 목적으로 사용할 공백 문자 수

### `JSON.parse`
- `let value = JSON.parse(str, [revier]);`
  - str: JSON 형식의 문자열
  - reviver: 모든 `(key, value)` 쌍을 대상으로 호출되는 __function(key, value)__ 형태의 함수로 값을 변경시킬 수 있음.
