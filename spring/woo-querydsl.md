## 우아한 형제들 `QueryDSL` 사용법
> [참고자료](https://velog.io/@youngerjesus/%EC%9A%B0%EC%95%84%ED%95%9C-%ED%98%95%EC%A0%9C%EB%93%A4%EC%9D%98-Querydsl-%ED%99%9C%EC%9A%A9%EB%B2%95)

### 1. extends / implements 사용하지 않기
```java
// 기존 방법 1. 
public interface MemberRepository extends JpaRepository<Member, Long>, MemberRepositoryCustom {} 


// 기존 방법2
public class MemberRepositoryCustom extends QuerydslRepositorySupport {}

// 추천하는 방법
@Repository
@RequiredArgsConstructor 
public class MemberRepositoryCustom {
    private final JpaQueryFactory queryFactory; // 물론 이를 위해서는 빈으로 등록을 해줘야 한다. 
}
```

### 2. 동적 쿼리 `BooleanExpression` 사용
- 재사용성이 높다
- `NULL` 반환 시, WHERE 절에서 조건이 무시되기 떄문 안전!


```java
public List<MemberTeamDto> searchByBuilder(MemberSearchCondition condition){
    BooleanBuilder builder = new BooleanBuilder();

    if (hasText(condition.getUsername())) {
        builder.and(member.username.eq(condition.getUsername()));
    }

    if(hasText(condition.getTeamName())){
        builder.and(team.name.eq(condition.getTeamName()));
    }

    if(condition.getAgeGoe() != null) {
        builder.and(member.age.goe(condition.getAgeGoe()));
    }

    if(condition.getAgeLoe() != null){
        builder.and(member.age.loe(condition.getAgeLoe()));
    }

    return queryFactory
            .select(new QMemberTeamDto(
                    member.id.as("memberId"),
                    member.username,
                    member.age,
                    team.id.as("teamId"),
                    team.name.as("teamName")
            ))
            .from(member)
            .leftJoin(member.team, team)
            .where(builder)
            .fetch();
}

Where 절과 BooleanExpression 을 이용하는 에제
public List<MemberTeamDto> searchByWhere(MemberSearchCondition condition){
    return queryFactory
            .select(new QMemberTeamDto(
                    member.id.as("memberId"),
                    member.username,
                    member.age,
                    team.id.as("teamId"),
                    team.name.as("teamName")
            ))
            .from(member)
            .leftJoin(member.team, team)
            .where(
                usernameEq(condition.getUsername()),
                teamNameEq(condition.getTeamName()),
                ageGoe(condition.getAgeGoe()),
                ageLoe(condition.getAgeLoe())
            )
            .fetch();
}

private BooleanExpression usernameEq(String username) {
    return hasText(username) ? member.username.eq(username) : null;
}

private BooleanExpression teamNameEq(String teamName) {
    return hasText(teamName) ? team.name.eq(teamName) : null;
}

private BooleanExpression ageGoe(Integer ageGoe) {
    return ageGoe != null ? member.age.goe(ageGoe) : null;
}

private BooleanExpression ageLoe(Integer ageLoe) {
    return ageLoe != null ? member.age.loe(ageLoe) : null;
}

private BooleanExpression ageBetween(Integer ageLoe, Integer ageGoe) {
    return ageLoe(ageLoe).and(ageGoe(ageGoe));
}
```

### 3. exist 메소드 사용하지 않기
- count 쿼리 사용하기 떄문
  - 전체 행 모두 조회

### 4. Cross Join 회피하기
- 묵시적 조인
- 조인을 명시하지 않고 엔터티에서 다른 엔터티 조회해서 비교하는 경우 JPA가 알아서 크로스 조인 하게 됨


```JAVA
Cross Join 발생 예제
public List<Member> crossJoin() {
    return queryFactory
            .selectFrom(member)
            .where(member.team.id.gt(member.team.leader.id))
            .fetch();
}
select
    member0_.member_id as member_i1_0_,
    member0_.age as age2_0_,
    member0_.team_id as team_id4_0_,
    member0_.username as username3_0_ 
from
    member member0_ cross 
join
    team team1_ 
where
    member0_.team_id=team1_.team_id 
    and member0_.team_id>team1_.member_id
Cross Join 을 InnerJoin 으로 변경하
public List<Member> crossJoinToInnerJoin() {
    return queryFactory
            .selectFrom(member)
            .innerJoin(member.team, team)
            .where(member.team.id.gt(member.team.leader.id))
            .fetch();
}
select
    member0_.member_id as member_i1_0_,
    member0_.age as age2_0_,
    member0_.team_id as team_id4_0_,
    member0_.username as username3_0_ 
from
    member member0_ 
inner join
    team team1_ 
        on member0_.team_id=team1_.team_id 
where
    member0_.team_id>team1_.member_id
```

### 5. 조회할땐 Entity 보다 `DTO` 우선적으로 가져오기
- 엔티티 사용 시 >> 영속성 컨텍스트의 1차 캐시 기능 사용


```JAVA
Dto 조회할때 필요한 칼럼만 가져오기
public List<MemberTeamDto> findSameTeamMember(Long teamId){
    return queryFactory
            .select(new QMemberTeamDto(
                    member.id,
                    member.username,
                    member.age,
                    Expressions.asNumber(teamId),
                    team.name
            ))
            .from(member)
            .innerJoin(member.team, team)
            .where(member.team.id.eq(teamId))
            .fetch();
}
```

### 6. select 칼럼에 entity 자제
```java
Select 절에 Entity가 있는 경우
public List<MemberTeamDto2> entityInSelect(Long teamId){
    return queryFactory
            .select(
                    new QMemberTeamDto2(
                            member.id,
                            member.username,
                            member.age,
                            member.team // team 에 있는 모든 칼럼을 가지고오게 된다. 
                    )
            )
            .from(member)
            .innerJoin(member.team, team)
            .where(member.team.id.eq(teamId))
            .fetch();
}
select
    member0_.member_id as col_0_0_,
    member0_.username as col_1_0_,
    member0_.age as col_2_0_,
    member0_.team_id as col_3_0_,
    team1_.team_id as team_id1_1_,
    team1_.member_id as member_i3_1_,
    team1_.name as name2_1_ 
from
    member member0_ 
inner join
    team team1_ 
        on member0_.team_id=team1_.team_id 
where
    member0_.team_id=?
Select 절에 필요한 칼럼만 넣자.
public List<MemberTeamDto2> entityInSelect(Long teamId){
    return queryFactory
            .select(
                    new QMemberTeamDto2(
                            member.id,
                            member.username,
                            member.age,
                            member.team.id // 꼭 필요한 칼럼만 가지고오자. 
                    )
            )
            .from(member)
            .innerJoin(member.team, team)
            .where(member.team.id.eq(teamId))
            .fetch();
}
```


### 기타 등등...
