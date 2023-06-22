## React `Snackbar`
> [참고자료](https://iborymagic.tistory.com/85)
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/a43f486e-4099-4835-9a96-25075b4f28ec)

### 개발 코드
```js
const Snackbar = ({ text, time, setMessage, backgroundColor }) => {
  const [isShowing, setIsShowing] = useState(true);
  const timer = setTimeout(() => setIsShowing(false), time);

  useEffect(() => {
    return () => {
      setMessage('');
      clearTimeout(timer);
    };
  }, [isShowing]);

  return (
    <Styled.SnackbarContainer backgroundColor={backgroundColor} time={`${time / 1000}s`}>
      {text}
    </Styled.SnackbarContainer>
  );
};

// 사용부
const [snackbarMessage, setSnackbarMessage] = useSnackbar(TIME.SNACKBAR_DURATION);
// ...
{snackbarMessage && (
  <Snackbar text={snackbarMessage} time={3000} setMessage={setSnackbarMessage} backgroundColor="#555" />
)}

..

const useSnackbar = (ms) => {
  const [message, setMessage] = useState('');
  const timer = useRef(null);

  useUpdateEffect(() => {
    if (timer.current) clearTimeout(timer.current);
    timer.current = setTimeout(() => {
      setMessage('');
    }, ms + 100); // add 100ms for fadeout animation
  }, [message]);

  useEffect(() => {
    return () => {
      clearTimeout(timer.current);
      setMessage('');
    };
  }, []);

  return [message, setMessage];
};
```



