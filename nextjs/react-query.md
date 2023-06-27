## react-query
> [참고자료](https://velog.io/@rmaomina/react-query-core-concept)
- `query key` 기반 >> 쿼리 캐시 관리
  - 직렬화 + 식별 가능 >> 고유한 값
### `useQeury`
- `query key` + 서버 데이터 >> 패치 >> `Promise` 리턴 >> ✔ `queryFn`
- 단, 서버 사이드 이펙트 유발 >> `useMutation()`
#### 속성
##### 1. isError
- error
##### 2. success
- 성공인 경우에만 데이터 가져옴
- data


```js
function Todos() {
  const { status, data, error } = useQuery({
    queryKey: ['todos'],
    queryFn: fetchTodoList,
  })

  if (status === 'loading') {
    return <span>Loading...</span>
  }

  if (status === 'error') {
    return <span>Error: {error.message}</span>
  }

  return (
    <ul>
      {data.map((todo) => (
        <li key={todo.id}>{todo.title}</li>
      ))}
    </ul>
  )
}
```
### 참고
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/42629dba-8402-4390-b71d-30aedcf2aa48)
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/0b9596b3-74af-4889-922b-a93ea884b890)



