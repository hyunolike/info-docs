## css 선택자
> [참고자료](https://www.nextree.co.kr/p8468/)
- 웹 표준 > 구조`html` + 표현`css` + 행위`javascript`
- 🐥선택자: 선택을 해주는 요소 / 특정 요소들을 선택하여 스타일 적용해주게 해줌11
### 기본이야
- 전체선택자
- 태그선택자
- 클래스 선택자
- ID 선택자
- 복합 선택자
  - 하위 선택자 `section ul {...}`
  - 자식 선택자 `section > ul {...}`
  - 인접 형제 선택자 `h1+ul {...}`
  - 일반 형제 선택자 `h1~ul {...}`
- 속성 선택자 👨‍🌾
- 가상 클래스 선택자 `Pseudo-Classes`👨‍🌾
- 그외 선택자 > 알면 좋아~~~
  - 언어 선택자 `E::lang(ko)`
  - 부정 선택자 `E::not(s)`
  - 목적 선택자 `E::target`
  - UI요소 상태 선택자
    - `E::enabled`
    - `E::disabled`
    - `E::checked`
  - 가상 엘리먼트 선택자 
### 👨‍🌾 속성 선택자
- <img width="824" alt="image" src="https://github.com/hyunolike/info-docs/assets/61215550/76f02149-e402-4de1-8bab-5d7ea819f9aa">
### 👨‍🌾 가상 클래스 선택자 
#### 1. 링크 선택자 & 동적 선택자
> 문서 안의 링크와 관련된 선택자
- <img width="798" alt="image" src="https://github.com/hyunolike/info-docs/assets/61215550/013aae40-9bb3-4ef8-8687-66bdb0719aa1">
#### 2. 구조적 가상 클래스 선택자 `Structural pseudo-classes`
> `위치` 기준으로 삼는다!
- <img width="868" alt="image" src="https://github.com/hyunolike/info-docs/assets/61215550/3385319b-8be2-41eb-955a-065d8d265a73">
### 👨‍🌾 선택자 우선순위
> 스타일 충돌 조심!
- css 원천 소스 3가지
  - 제작자 원천 소스: 웹 사이트 제작자가 지정하는 자신의 페이지 스타일
  - 사용자 원천 소스: 사용자가 직접 정하는 자신이 사용할 스타일
  - 사용자 도구 소스: 웹 브라우저 자체에 지정된 기본 스타일
#### 1. 원천소스 우선 순위
1. `!important` 선언을 한 사용자 스타일
2. `!important` 선언을 한 제작자 스타일
3. 제작자 스타일
4. 사용자 스타일
5. 사용자 도구 스타일 (브라우저 자체의 선언)
#### 2. css 명시도`Specificity` 계산법
> 아래 대괄호 점수로 계산


```
!important > id [100] > class [10] > tag [1] > * [0]
```


