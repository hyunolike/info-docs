## UUID Universal Unique Identifier 범용 단일 식별자
> [참고자료](https://zivvle.tistory.com/entry/%EB%A6%AC%EC%95%A1%ED%8A%B8-%EA%B3%A0%EC%9C%A0%ED%95%9C-Key-%EA%B0%92-%EC%83%9D%EC%84%B1%ED%95%98%EA%B8%B0-uuid)

- ⭐리엑트 반복되는 컴포넌트 >> 고유한 key 지정 필요
- `uuid` >> 고유한 키 값 간편 생성 라이브러리


```js
import {v4} from "uuid";
v4(); // 4b39fj-32f4-84dj-2nf0-4w5aff39j

// v4를 uuidv4라는 이름으로 사용
import {v4 as uuidv4} from "uuid";
uuidv4();
```
