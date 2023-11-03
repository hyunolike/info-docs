## `react-query` 사용하기
> [참고자료](https://velog.io/@eeeve/React-Query)
### 요약
1. `useQuery` 조회 기능
2. `useMutation` 업데이트, 수정 기능
### 베이스 코드
```js
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
