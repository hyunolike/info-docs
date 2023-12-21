## `react-query` 동기처리
> [참고자료](https://velog.io/@ahuuae/Library-React-Query)

- `enabled` 속성 사용
- `useQuery` > enabled 속성 true 인 경우 실행!


```js
const fetchUserByEmail = (email) => {
  return axios.get(`http://localhost:4000/users/${email}`);
};

const fetchCoursesByChannelId = (channelId) => {
  return axios.get(`http://localhost:4000/channels/${channelId}`);
};

const DependentQueries = ({ email }) => {
  const { data: user } = useQuery(['user', email], () => fetchUserByEmail(email));
  const channelId = user?.data.channelId;

  // 집중❗️ 이중 부정을 통해서 channelId이 true -> useQuery 실행, false -> 실행 X
  useQuery(['courses', channelId], () => fetchCoursesByChannelId(channelId), {
    enabled: !!channelId,
  });
  return <div>DependentQueries</div>;
};

export default DependentQueries;
```
