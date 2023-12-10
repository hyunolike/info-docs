## `routeChange event` 페이지 로딩 UI 구현
> [참고자료](https://vroomfan.tistory.com/58)

### 상황
- 페이지 전환되는 동안 페이지 중앙에 로딩 ui 그려줄래
- 모든 페이지 해당 기능 > 커스텀 `_app.js` 파일에서 처리 방법 고안

### 해결방법
#### 로딩
```js
// Loading.jsx
import React from 'react';
import styled from '@emotion/styled';
import useSWR from 'swr';
import { LOADING_KEY } from '../swr/loading';
import Image from 'next/image';

const Loading = () => {
  const { data: loading } = useSWR(LOADING_KEY);

  if (!loading) return null;
  return (
    <FullContainer>
      <Image src="/loading.png" alt="" width={100} height={100} />
    </FullContainer>
  );
};

export default Loading;

const FullContainer = styled.div`
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  
  ...
`;
```
#### `Router.events listner`
```js
  // _app.js
function MyApp({ Component, pageProps }) {
  ...
  // page transition
  useEffect(() => {
    const start = () => {
      mutate(LOADING_KEY, true);
    };
    const end = () => {
      mutate(LOADING_KEY, false);
    };

    Router.events.on('routeChangeStart', start);
    Router.events.on('routeChangeComplete', end);
    Router.events.on('routeChangeError', end);

    return () => {
      Router.events.off('routeChangeStart', start);
      Router.events.off('routeChangeComplete', end);
      Router.events.off('routeChangeError', end);
    };
  }, []);

  return (
    <>
      ...
      <Component {...pageProps} />
      <Loading />
      ...
    </>
  );
}

export default MyApp;
```
