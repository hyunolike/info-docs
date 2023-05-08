## YAML 문법
> [참고자료](https://lejewk.github.io/yaml-syntax/) <br>
> [JOSN TO YAML](https://www.json2yaml.com/)
- `#`: 주석
- `---`: 문서의 시작
- `...`: 문서의 끝

### 1. 기본 표현
- `KEY : VALUE`

### 2. 자료형
- `int` `string` `boolean`
- `object`
- `list`
- `text`

```yml
# object
key: 
  key: value
  key: value

# 또는

key: {
  key: value,
  key: value
}

# list
key:
  - item
  - item

# 또는

key: [
  item, item
]

# text
--- # 문서의 시작
# my test yaml syntax

name: wook
job: developer

basic_list:
- apple
- banana
- orange

another_list: [
  apple, 
  banana, 
  orange
]

object_list:
- color: red
  direction: left
- color: blue
  direction: right

basic_object: 
  time: '12:34:11'
  date: '2019-04-30'

another_object: {
  time: '12:34:11',
  date: '2019-04-30'
}

comment_line_break: |
  Hello my name is wook.
  Im developer.

comment_single_line: >
  Hello world
  my first yml syntax.

... # 문서의 끝
```
