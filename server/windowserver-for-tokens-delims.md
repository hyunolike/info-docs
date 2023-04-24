## 윈도우 서버 - for문 문자열 추출
> [참고자료](https://ikcoo.tistory.com/370)

### `token` 문법
- for문 각 행별 분석
- token: 각 행의 몇 번째 문자열 전달해줄지 지정
  - ✔ `tokens`의 의미 >> 공백을 기준으로 문자열 나눔

```shell
@echo off

for /f "tokens=2" %%a in ('type test.log') DO set result=%%a (
   echo %result
)
```
### delims 문법
- 지정한 구분 문자로 구분


```shell
@echo off

for /f "tokens=2 delims='='" %%a in ('type test.log') DO set result=%%a (
   echo %result%
)
```
- ![image](https://user-images.githubusercontent.com/61215550/233878728-4912761e-2df4-478b-95cf-a192ff482aef.png)
