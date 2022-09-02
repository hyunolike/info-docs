## `Redux` `Recoil`
> [참고자료](https://itchallenger.tistory.com/539)
### 요약
- `Redux` `Recoil` >> react를 위한 상태관리 라이브러리
- ✔ `Redux`: Flux 아키텍쳐 기반 
- ✔ `Recoil`: Atomic 모델 기반(Atom 이란 작은 상태 단위로 관리 / Atom 결합해 데이터 가공)


|Redux|Recoil|
|-------|--------|
|![image](https://user-images.githubusercontent.com/61215550/188076179-3b915fbf-2eff-49b0-8893-089073992957.png)|![image](https://user-images.githubusercontent.com/61215550/188076164-cb60c974-d8f7-4aad-bde5-9dc40e89b144.png)|
### Redux - 중앙 집중식
> [참고자료](https://velog.io/@katanazero86/redux-recoil-%EB%82%B4%EC%9A%A9-%EC%A0%95%EB%A6%AC)
- ![image](https://user-images.githubusercontent.com/61215550/188076493-3ec2633e-24ce-4e57-9222-b2b56d0b418b.png)

### Recoil
- `Atom` 상태 단위로 관리 >> 컴포넌트는 이것만 구독하면 됨!
- 저장소 개념보다 작은 상태 단위로 관리
- 상태 변경으로 인한 불필요한 렌더링 발생 x 
  - 상태 구독한 컴포넌트만 리렌더링 발생ㅎ
- `selector` 통해 캐싱(기본적으로 값 캐싱)


|용어|설명|
|-----|-----|
|`Atom`|데이터 조각 / 상태 조각|
|`Selector`|1. 아톰에서 파생된 데이터 조작 <br>2. 데이터 반환하는 순수 함수|

