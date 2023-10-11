## `react.js` children에 props 전달
> [참고자료](https://guiyomi.tistory.com/128)


```js
import {Children, cloneElement, isValidElement, useEffect, useState} from "react";

const Layout = ({ children }) => {
  const childrenWithProps = Children.map(children, (child) => {
    if (isValidElement(child)) {
      return cloneElement(child, { 추가할_PROPS_이름: 'PROPS_값' });
    }
    return child;
  });

  return <div className={classes.card}>{childrenWithProps}</div>;
};

export default Layout;
```
