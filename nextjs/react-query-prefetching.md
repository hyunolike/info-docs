## `react query` pre fetching
> [참고자료](https://choi-hyunho.tistory.com/104) <br>
> [참고자료2](https://velog.io/@pjh1011409/React-Query-Pagination-Pre-fetching)
- ⭐ 데이터 미리 가져오기 > 캐시 > `사용자 경험 개선`
- 데이터 미리 채울래~~

### 데이터 미리 채우는 방법
#### 1. `prefetchQuery`
- 서버로부터 받아온 데이터 캐시에 추가
#### 2. `setQueryData`
- useQuery 실행 x > 쿼리 데이터 캐시에 추가하는 또다른 방법
- 단, 클라이언트에서 데이터 받아옴 / 서버에서는 `mutation` 된 상태의 데이터 일것!
#### 3. `placeholderData`
- `useQuery` 옵션 > 실행 시 데이터 제공
- 임시로 채워놓는 표시용 데이터
#### 4. `initialData`
- `useQuery` 옵션
- `placeholderData` 랑 반대 개념
- 캐시에 추가해야하는 데이터 존재

### Prefetching
- 데이터 미리 캐시!
  - 기본값 `만료(stable)` 상태
- 즉, 데이터 사용 > 만료 상테에서 가져옴
- 데이터 가져오는 중 > 캐시에 있는 데이터 이용해 화면에 나타냄!
- ✔ 추후 사용자 사용할만한 데이터 > 프리패칭!

### 사용
```javascript
// 컴포넌트 가져올때
const queryClient = useQueryClient();

// 페이지 변경 시 실행
useEffect(() => {
  const nextPage = currentPage + 1;
  queryClient.prefetchQuery();
})
```
#### `keepPreviousData`
- 쿼리 키 바뀔 때도 지난 데이터 유지


```javascript
const {data, isLoading, isError, error} = useQuery(['posts'], currentPage],
() => fetchPosts(currentPage), {staleTime: 2000, keepPreviousData: true});
```

