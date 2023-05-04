## SnakeYAML 
> [참고자료](https://ivvve.github.io/2018/12/05/java/Spring/snake_yaml/)
- 자바용 YAML 처리기

### 스프링부트 내 YAML 파일 프로퍼티 매핑할 수 있는 이유
- `SnakeYAML` 라이브러리 사용하기 떄문 ⭐

### YAML 소개
> [참고자료](https://zetawiki.com/wiki/YAML)
- 데이터 교환 형식의 하나
- 사람이 읽을 수 있도록 정한 데이터 직렬화 형식
- 모든 데이터를 `리스트` `해쉬` `스칼라` 데이터의 조합으로 표현

#### 1. 리스트
```yml
--- # Favorite movies, block format
- Casablanca
- Spellbound
- Notorious
--- # Shopping list, inline format
[milk, bread, eggs]
```

#### 2. 해시
```yml
--- # Block
name: John Smith
age: 33
--- # Inline
{name: John Smith, age: 33}
```
#### 3. 블록 리터럴
##### 3-1. 개행 보존
```yml
--- |
  There was a young fellow of Warwick
  Who had reason for feeling euphoric
      For he could, by election
      Have triune erection
  Ionic, Corinthian, and Doric

```
##### 3-2. 개행 무시
```yml
--- >
  Wrapped text
  will be folded
  into a single
  paragraph
  
  Blank lines denote
  paragraph breaks

```
#### 4. 해시의 리스트
```yml
- {name: John Smith, age: 33}
- name: Mary Smith
  age: 27

```
#### 5. 리스트의 해시
```yml
men: [John Smith, Bill Jones]
women:
  - Mary Smith
  - Susan Williams

```
