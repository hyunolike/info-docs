## `QueryDSL` @QueryProjection
> [참고자료](https://ttl-blog.tistory.com/226)
### 프로젝션
- ✔ `select` 절에 대상을 지정하는 것
- 엔티티와 다른 반환 타입일 경우 사용

### `@QueryProjection` - 💡 가장 좋은 방법
> [참고자료](https://cheese10yun.github.io/querydsl-projections)
- DTO 생성자 + `@QueryProjection`
  - 컴파일 시 타입 체크
  - DTO까지 `Q파일` 생성

```java
.select(QMemberDto( // QMemberDtoQueryProjection 의 생성자를 이용한다.
    qMember.username,
    qMember.age
))
```

### 1. DTO 조회 - `Projection`
- 3가지 방법
  - 프로퍼티 접근 `setter`: setter & 기본 생성자 필수
  - 필드 직접 접근: 기본 생성자 필수
  - 생성자 사용: 타입이 일치하는 생성자 필수

#### 1-1. 프로퍼티 접근
- `Projections.bean()`

#### 1-2. 필드 직접 접근
- `Projections.fields()`
- DTO와 Entity의 필드명이 다른 경우
  - `ExpressionUtils.as(source , alias)`: 필드나 서브 쿼리에 별칭 적용
  - `username.as(alias)`: 필드에 별칭 적용
#### 1-3. 생성자 사용
- `Proections.contrutor()`
