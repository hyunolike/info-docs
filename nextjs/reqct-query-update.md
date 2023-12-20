## `react query` - Mutation, useMutation
> [참고자료](https://velog.io/@tkdals0978/React-Query-Mutation%EA%B3%BC-useMutation)

### Mutation
- 서버에 데이터 업데이트하도록 네트워크 호출! ⭐
  - `useQuery` > CREATE
  - `useMutation` > READ/UPDATE/DELETE
- `Optimistic UI`
  - 서버 전송이 잘되거라 판단하고 즉시 변화!
- 쿼리 무효화 `invalidation`
  - 서버 리패치 > 클라이언트 있는 데이터 >> 서버의 데이터와 최신상태로 유지
 
### useMutation
- `mute` 함수 반환
  - 변경사항 토대로 서버 호출
- 데이터 저장안하므로 `쿼리키` ❌


```
// useMutation
const {
  data,
  error,
  isError,
  isIdle,
  isLoading,
  isPaused,
  isSuccess,
  mutate,
  mutateAsync,
  reset,
  status,
} = useMutation(mutationFn, {
  cacheTime,
  mutationKey,
  networkMode,
  onError,
  onMutate,
  onSettled,
  onSuccess,
  retry,
  retryDelay,
  useErrorBoundary,
  meta
})

// mutate함수
mutate(variables, {
  onError,
  onSettled,
  onSuccess,
})
```

- ![image](https://github.com/hyunolike/info-docs/assets/61215550/da6258aa-b124-4fbb-8486-cdec8c643d46)
