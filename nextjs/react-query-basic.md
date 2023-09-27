## `react query` 서버 데이터 관리
> [참고자료](https://velog.io/@kimhyo_0218/React-Query-%EB%A6%AC%EC%95%A1%ED%8A%B8-%EC%BF%BC%EB%A6%AC-%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-useQuery)

### 기본 셋팅
```javascript
import { QueryClient, QueryClientProvider } from "react-query";

const queryClient = new QueryClient();

export default function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <Home />
    </QueryClientProvider>
  );
}
```
### 1. `useQuery`
- `read` 작업 할떄 사용하는 훅
- ⭐첫번째 파라미터 `QueryKey` / 두번째 파라미터 `비동기 함수(api 호출 함수)`
- 비동기 방식
  - 여러 개의 비동기 쿼리 존재 시 > `useQueries` 사용 지향

#### 1-1. `Query Key`
- 쿼리 키 기반 > 데이터 캐싱 관리
- 문자열 / 배열 지정 가능
- ⭐쿼리키를 배열로 지정하면 배열의 0번 값은 string으로 다른 컴포넌트에서 부를 키를 넣어주면 되고 1번째 값은 query함수의 파라미터로 전달될 값을 넣어주면 된다.
#### 1-2. `Query Functions`
- `promise` 반환하는 함수

#### 1-3. `Query Options`
> [공식자료](https://tanstack.com/query/v4/docs/react/reference/useQuery?from=reactQueryV3&original=https%3A%2F%2Freact-query-v3.tanstack.com%2Freference%2FuseQuery)
- `enabled (boolean)`
  - 쿼리 자동 실행 안되도록
- ...

### 2. `useMutation`
- 데이터 변경 및 삭제하는 메서드


```javascript
const data = useMutation(API 호출 함수, 콜백);
```
