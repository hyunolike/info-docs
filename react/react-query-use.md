## `react-query` 사용하기
> [참고자료](https://velog.io/@eeeve/React-Query)
### 요약
1. `useQuery` 조회 기능
2. `useMutation` 업데이트, 수정 기능
### 베이스 코드
```js
// 버튼 클릭될때 동작되랏
const {data, refetch} = useQuery(["id", id],
  서버 데이터 조회 로직,
  {
    refetchOnWindowFocus: false,
    enabled: !!id // id 없으면 조회 안해!
  }
)

...

const onSearch = () => {
  refetch();
}
```
### 개념 설명
#### 1. `useQuery` read 기능! ✔
- 첫번쨰 파라미터 > `QueryKey` 들어가
- 두번째 파라미터 > 비동기 함수 (API 호출 함수)
- RETURN 값 > API 성공/실패 여부, API 리턴 값 포함한 객체
- `비동기` 동작!
  - 만약, `useQuery` 2개 이상이면 이거 모두 `동시`에 실행돼! 😛
  - `useQueries` 사용하는 거 권장이야


```js
import { useQuery } from "react-query";

// 주로 사용되는 3가지 return값 외에도 더 많은 return 값들이 있다.
const { data, isLoading, error } = useQuery(queryKey, queryFn, options)
```
##### 1-1. Query Options
- `enabled` (boolean)
  - 쿼리가 자동으로 실행되지 않게 하는 옵션
- `retry` (boolean | number | (failureCount: number, error: TErro) => boolean)
  - 기본 3회
  - 실패한 쿼리 재시도하는 옵션
  - true > 무한 재시도 / false > 재시도 하지 않음
- `staleTime` (number | Infinity)
  - 기본 0
  - 해당 시간 지나면 > `stale` 상태 됨!
  - 데이터가 fresh 상태로 유지되고 .. .시간이다아아
  - 💡 fresh 상태 > 다시 mount되도 fetch 실행 x
- `cacheTime` (number | Infinity)
  - 기본 5분
  - `inactive` 상태인 캐시 데이터가 메모리에 남아있는 시간!
  - 시간 지나면 캐시데이터 `가비지 컬렉터` 에 의해 메모리에서 제거!
- `refetchOnWindowFocus` (boolean | "always")
  -   기본 true
  -   윈도우 포커싱 마다 refetch 실행하는 옵션
  -   `always` 설정 > 항상 윈도우 포커싱 때 마다 refetch!
 
... 
#### 2. `useMutation` 데이터 변경 및 삭제하는 메서드
- `post` `put` `delete` 같은 변경 및 수정 작업 시 사용되는 훅



```js
const data = useMutation(API 호출 함수, 콜백);
```


- 쿼리 무효화 `invalidation`
  - add 후 수동적으로 패치해줘야 화면에 보여진다는 불편함 존재 ? 쿼리 무효화를 하자??


