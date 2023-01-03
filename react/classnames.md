## classnames
> [참고자료](https://velog.io/@jinhengxi/React-classnames)
- `yarn add classnames`



```js
import classNames from ‘classnames’;


classNames(‘one’, ‘two’); // = ‘one two‘
classNames(‘one’, { two: true }); // = ‘one two‘
classNames(‘one’, { two: false }); // = ‘one‘
classNames(‘one’, [‘two’, ‘three’]); // = ‘one two three‘
```
