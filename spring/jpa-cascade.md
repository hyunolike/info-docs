## JPA - CASCADE 영속성 전이
> [참고자료](https://velog.io/@devsh/JPA-CASCADE-%EC%98%81%EC%86%8D%EC%84%B1-%EC%A0%84%EC%9D%B4)

### 1. 언제 사용?
- 하나의 부모 >> 여러 자식들 관리할 때(단일 엔티티 종속적인 경우)
- 라이프사이클이 같을 때, 단일 소유자

### 주요 옵션
- 실무에서 주요 사용하는 옵션 `ALL` `PERSIST`


|옵션|설명|
|----|-----|
|`ALL`|모두 적용|
|`PERSIST`|영속|
|`REMOVE`|삭제|
|`MERGE`|병합|
|`REFRESH`|REFRESH|
|`DETACH`|DETACH|
