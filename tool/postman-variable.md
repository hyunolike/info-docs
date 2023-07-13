## 포스트맨 변수
> [참고자료](https://inpa.tistory.com/entry/POSTMAN-%F0%9F%92%BD-%ED%8F%AC%EC%8A%A4%ED%8A%B8%EB%A7%A8-%EB%B3%80%EC%88%98-%EC%82%AC%EC%9A%A9-%EB%B0%A9%EB%B2%95-%ED%99%98%EA%B2%BD-%EB%B3%80%EC%88%98-%EC%A0%84%EC%97%AD-%EB%B3%80%EC%88%98)
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/a1571ab2-2433-4bd6-a4b7-d8fa7c1c4406)
- 프로그래밍 일반적인 변수
### ✔ 포스트맨 변수 5가지 유형
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/3e68515f-96c1-4282-9ee3-37e90361a555)
#### 01 환경변수
- `KEY-VALUE`
- KEY >> 변수
- json 파일 저장 가능
- 환경변수 사용
  - 오른쪽 상단 환경 선택
#### 02 전역변수
- 모든 범위 사용


```js
pm.environment.set('환경변수명'); // 환경변수 만들기
pm.environment.get('환경변수명'); // 환경변수 가져오기

pm.globals.set('전역변수명'); // 전역변수 만들기
pm.globals.get('전역변수명'); // 전역변수 가져오기
```
