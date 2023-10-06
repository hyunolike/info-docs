## `styled components` 태그 속성 추가 방법
> [공식자료](https://styled-components.com/docs/api#attrs)
### `attrs`
```js
const Input = styled.input.attrs(props => ({
  type: 'text',
  size: props.$small ? 5 : undefined,
}))<{ $padding?: string; $small?: boolean; }>`
  border-radius: 3px;
  border: 1px solid #BF4F74;
  display: block;
  margin: 0 0 1em;
  padding: ${props => props.$padding};

  ::placeholder {
    color: #BF4F74;
  }
`
```


### 추가
#### 1. 기본 내보내기
- `styled.tagname`



```js
// import styled from 'styled-components'

const Button = styled.button`
  background: #BF4F74;
  border-radius: 3px;
  border: none;
  color: white;
`

const TomatoButton = styled(Button)`
  background: tomato;
`

render(
  <>
    <Button>I'm purple.</Button>
    <br />
    <TomatoButton>I'm red.</TomatoButton>
  </>
)
```
##### 2. TaggedTemplateLiteral
- 템플릿 사이사이에 들어가는 자바스크립트 객체 / 함수의 원본값 그대로 출력 가능


```js
// import styled from 'styled-components'

const padding = '3em'

const Section = styled.section<{ $background?: string; }>`
  color: white;

  /* Pass variables as inputs */
  padding: ${padding};

  /* Adjust the background from the properties */
  background: ${props => props.$background};
`

render(
  <Section $background="royalblue">
    ✨ Magic
  </Section>
)
```
