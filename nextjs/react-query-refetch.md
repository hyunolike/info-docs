## react qeury - `useQuery` refetch
> [참고자료](https://velog.io/@rmaomina/useQuery-refetch-options)
- useQuery 3가지 옵션
  - 고유 `query key`
  - promise 리턴 `queryFn`
  - 😛 캐시 상태 `refetch`
### `staleTime`
> staleTime: number | Infinity
- 클라이언트 불러온 서버 데이터 얼마나 오래 됐는지(stale)
- fresh 상태 얼마나 유지
- 기본값 `0`


```js
const { isLoading, isError, data } = useQuery<IHistorical[]>(
  ["ohlcv", coinId],
  () => fetchCoinHistory(coinId),
  {
    staleTime: 5000, ⭐ 5000ms
  },
);
```
### cacheTime
> cacheTime: number | Infinity


```js
const { isLoading, isError, data } = useQuery<IHistorical[]>(
  ["ohlcv", coinId],
  () => fetchCoinHistory(coinId),
  {
    cacheTime: 5000,
  },
);
```
### refetchInterval
> refetchInterval: number | false | ((data: TData | undefined, query: Query) => number | false)
- 주기적으로 서버의 데이터 동기화 필요할때


```js
const { isLoading: priceLoading, data: priceData } = useQuery<ICoinPrice>(
    ["price", coinId],
    () => fetchCoinPrice(coinId),
    {
      refetchInterval: 5000,
      refetchIntervalInBackground: true, ⭐브라우저 포커싱 안되도 백그라운드에서 실행
    },
  );
```
### refetchOnWindowFocus
> refetchOnWindowFocus: boolean | "always" | ((query: Query) => boolean | "always")
- 앱(윈도우) 벗어났다가 다시 돌아올 경우 실행
