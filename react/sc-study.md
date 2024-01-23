## `styled-component` 똑똑하게 쓰기
> [참고자료](https://sangjuntech.tistory.com/m/11)
- 😃 `css-in-js` 대표적인 라이브러리
### 1. `props` 전달
```js
const SubTitleFont = styled.h2`
    font-size: ${(props) => props.fontSize};
    font-weight: 600;
`

fuction App () {
	return (
    	<section>
        	<SubTitleFont fontSize="22px">부제목1</SubTitleFont>
            <SubTitleFont fontSize="24px">부제목2</SubTitleFont>
        </section>
    )
}
```
### 2. `attr`
```js
const ProdImage = styled.img.attrs({ alt='제품 이미지' })`
    width: 100px;
    height: 100px;
`

function ProductItem() {
	return (
    	<MainContainer>
            <ProdImage src='https://*****'/>
            <ProdImage src='https://*****2'/>
            <ProdImage src='https://*****3' />
        </MainContainer>
    )
}
```
### 3. 확장 
```js
const Memo = styled.div`
    width:300px;
    height:500px;
`

const ShadowMemo = styled(Memo)`
    box-shadow: 2px 4px 8px;
`

funtion Section2 () {
  return(
    <MainContainer>
      <Memo>Lorem Ipsum</Memo>
      <ShadowMemo>Lorem Ipsum</ShadowMemo>
    </MainContainer>
  )
}
```
### 4. 유용한 선택자
```js
const Memo = styled.div`
    width:300px;
    height:500px;
`

const MainContainer = styled.section`
    display:flex;
    width:100vw;
    ${Memo} {
      background-color:black;
      color: white;
    }
`

const ShadowMemo = styled(Memo)`
    box-shadow: 2px 4px 8px;
`

funtion Section2 () {
  return(
    <>
    <MainContainer>
      <Memo>Lorem Ipsum</Memo>
      <ShadowMemo>Lorem Ipsum</ShadowMemo>
    </MainContainer>
      <Memo>Lorem Ipsum</Memo>
    </>
  )
}
```
