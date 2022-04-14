## 오라클 `NUMBER` 타입
> [참고 자료](https://bebeya.tistory.com/entry/ORACLE-Number-%ED%83%80%EC%9E%85-%ED%98%95%ED%83%9C-%ED%91%9C-Number25Number52)
- `NUMBER(p,s)` 
  - `p(percision, 정밀도)` : __최대 유효숫자 자릿수__ 나타냄 
  - `s(scale)` : 소수점 기준 자릿수

### 세부 설명
- `p(percision, 정밀도)`
- 예시 `NUMBER(1)` >>> 1 ⭕ / 123 ❌
  - 소수점 기준 모든 유효숫자 자릿수 의미
  - 만약 p에 명시한 것보다 큰 숫자값을 입력하면 오류 발생
- `s(scale)`
  - 양수면 소수점 이하
  - 음수면 소수점 이상
  - s에 명시한 숫자 이상의 숫자를 입력하면, s에 명시된 숫자로 반올림 처리
  - s 음수면 소수점 기준 왼쪽 자릿수만큼 반올림
  - s가 p보다 크면 p는 소수점 이하 유효숫자 자릿수 의미

![image](https://user-images.githubusercontent.com/61215550/163288748-2033b555-7141-4b75-8106-5f92573a22c7.png)

