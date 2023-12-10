## 페이지 전환 애니메이션
> [참고자료](https://velog.io/@sds11609/nextjs-%ED%8E%98%EC%9D%B4%EC%A7%80-%EC%A0%84%ED%99%98-%EC%95%A0%EB%8B%88%EB%A9%94%EC%9D%B4%EC%85%98-%EC%A3%BC%EA%B8%B0)
- 👨‍🌾 사용 라이브러리: `react-transition-group`
- ⭐️ `nextjs`
  - 기본 동작 > paqes directory 안의 page component >> `_app.tsx` 공통적으로 감싸준다!

### AppLayout.tsx
```js
import React, { ReactNode } from "react";
import Link from "next/link";
import { Transition, TransitionGroup } from "react-transition-group";
import { useRouter } from "next/router";
interface Props {
  children: ReactNode;
}
const TIMEOUT = 100;
const getTransitionStyles = {
  entering: {
    position: `absolute`,
    opacity: 0,
  },
  entered: {
    transition: `opacity ${TIMEOUT}ms ease-in-out, transform ${TIMEOUT}ms ease-in-out`,
    opacity: 1,
  },
  exiting: {
    transition: `opacity ${TIMEOUT}ms ease-in-out, transform ${TIMEOUT}ms ease-in-out`,
    opacity: 0,
  },
};
const AppLayout = ({ children }: Props) => {
  const router = useRouter();
  return (
    <>
      <div>
        <Link href="/">
          <a>HOME</a>
        </Link>
        <Link href="/mypage">
          <a>MY_PAGE</a>
        </Link>
        <Link href="/contact">
          <a>CONTACT</a>
        </Link>
      </div>
      <TransitionGroup style={{ position: "relative" }}> ✅
        <Transition ✅
          key={router.pathname}
          timeout={{
            enter: TIMEOUT,
            exit: TIMEOUT,
          }}
        >
          {(status) => (
            <div
              style={{
                ...getTransitionStyles[status], ✅
              }}
            >
              {children}
            </div>
          )}
        </Transition>
      </TransitionGroup>
    </>
  );
};

export default AppLayout;
```
### state (`getTransitionStyles`)
- `entering`: 렌더 되기전 상태
- `entered`: 렌더 후 상태
- `exiting`: 화면에서 사라질 때

  
