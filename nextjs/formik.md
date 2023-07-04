## formik
> [참고자료](https://velog.io/@hjkdw95/Formik%EA%B3%BC-Yup%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EC%97%AC-input-validation-%EA%B0%84%ED%8E%B8%ED%95%98%EA%B2%8C-%EC%B2%98%EB%A6%AC%ED%95%98%EA%B8%B0)
- `form control` 기능 라이브러리
  - `re-render..` 이슈, state 처리
### 사용 `useFormick`
#### `initialValues`
- `form` 관리할 값들 모아놓은 객체
#### `validate`
- `validation` 확인 로긱 담아둠
#### `onSubmit`
- `submit` 이벤트 발생 시 실행할 로직 기재
### `Schema Validation with `Yup` 
- 유효성 체크 ⭐


```js
const formik = useFormik({
    initialValues: {
      email: 'demo@devias.io',
      password: 'Password123'
    },
    validationSchema: Yup.object({
      email: Yup
        .string()
        .email(
          'Must be a valid email')
        .max(255)
        .required(
          'Email is required'),
      password: Yup
        .string()
        .max(255)
        .required(
          'Password is required')
    }),
    onSubmit: () => {
      router.push('/');
    }
  });
```
