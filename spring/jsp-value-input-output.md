## jsp 프런트, 백 값(데이터) 전달 방법
> [참고자료](https://admm.tistory.com/54)
### 1. JSP --> Controller
- `Form-Action` 방식
- `Ajax` 방식

### 2. Controller --> JSP
- `Model` 객체
- `Redirect`
- `ResponseBody`

### 정리
|분류|방법|설명|
|---|----|----|
|JSP --> Controller|`Form-Action`|![image](https://user-images.githubusercontent.com/61215550/204173348-8959e9b5-26ff-4d0a-97cc-901984b1dcd5.png)|
| .. |`Ajax`|![image](https://user-images.githubusercontent.com/61215550/204173378-96fedab8-813b-48b0-8333-d4e2a3d46a9c.png)|
|Controller --> JSP|`Model Object`|![image](https://user-images.githubusercontent.com/61215550/204173446-be9dcbc2-2a26-4eb7-a657-be9d201bd4fa.png)|
| .. |`Redirect`|![image](https://user-images.githubusercontent.com/61215550/204173480-275713d1-978e-4cb4-847d-8e6725e01109.png)|
| .. |`ResponseBody`|![image](https://user-images.githubusercontent.com/61215550/204173507-50666865-af30-4462-9477-0c5e3b1d63be.png)|
