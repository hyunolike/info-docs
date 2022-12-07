## Vue Life Cycle
> [참고자료](https://hyeooona825.tistory.com/40)
- ![image](https://user-images.githubusercontent.com/61215550/206082374-6725170b-88bb-4b0f-afa6-8aec0e798c00.png)
- ⭐생명주기: 인스턴스의 상태에 따라 호출할 수 있는 속성들
  - 뷰의 인스턴스가 생성되어 소멸되기까지 거치는 과정!


```
data 속성의 초기화 및 관찰(Reactivity 주입)
뷰 템플릿 코드 컴파일(Virtual DOM -> DOM 변환)
인스턴스를 DOM에 부착
```
#### ✔ 라이프 사이클 훅
> [참고자료](https://joshua1988.github.io/vue-camp/vue/life-cycle.html#%E1%84%85%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%91%E1%85%B3-%E1%84%89%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%8F%E1%85%B3%E1%86%AF-%E1%84%83%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%A5%E1%84%80%E1%85%B3%E1%84%85%E1%85%A2%E1%86%B7)
- 인스턴스의 특정 시점에 원하는 로직을 구현할 수 있음
- 자주 사용되는 라이프 사이클 훅 목록
  - `created` `beforeMount` `mounted` `destroyed`

