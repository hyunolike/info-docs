## 클라이언트 오류 처리
> [참고자료](https://nextjs.org/docs/pages/building-your-application/configuring/error-handling#handling-client-errors)
- ✔ 서버?컴포넌트와의 렌더링 오류 발생 >> UI 제거 >> Application error 발생
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/bbcad8d2-bd77-472f-8cee-ba53d196924a)
### 에러 페이지 개발
#### 주요 constructor 메서드
- `getDerivedStateFromError(nextProps, prevState)`
  - props 받아온 값 >> state 동기화 하는 용도 (마운트 / 업데이트)
- `componentDidCatch(error, errorInfo)`
  - 컴포넌트 렌더링 중 애플리케이션 먹통 x / 오류 UI 잡아줌
- `render()`
  - UI 렌더링
 
#### 1. 직접 코드 작성
```js
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props)
 
    // Define a state variable to track whether is an error or not
    this.state = { hasError: false }
  }
  static getDerivedStateFromError(error) {
    // Update state so the next render will show the fallback UI
 
    return { hasError: true }
  }
  componentDidCatch(error, errorInfo) {
    // You can use your own error logging service here
    console.log({ error, errorInfo })
  }
  render() {
    // Check if the error is thrown
    if (this.state.hasError) {
      // You can render any custom fallback UI
      return (
        <div>
          <h2>Oops, there is an error!</h2>
          <button
            type="button"
            onClick={() => this.setState({ hasError: false })}
          >
            Try again?
          </button>
        </div>
      )
    }
 
    // Return children components in case of no error
 
    return this.props.children
  }
}
 
export default ErrorBoundary
```
#### 2. 라이브러리 사용
> [참고자료](https://react.dev/reference/react/Component#catching-rendering-errors-with-an-error-boundary)
- [바로가기](https://github.com/bvaughn/react-error-boundary)

