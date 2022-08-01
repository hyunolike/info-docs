## DB 형상관리
- [NHN Cloud](https://meetup.toast.com/posts/173)

## `Flyway`
> [참고 자료](https://sabarada.tistory.com/193)
- DB 형상관리 목적으로 하는 툴
- ![image](https://user-images.githubusercontent.com/61215550/178890336-db4d3b60-dc37-42ad-ba84-c9373107a683.png)

### 1. 스프링 부트 적용 방법
#### 1.1 의존성 및 환경 설정
`implementation("org.flywaydb:flyway-core:6.5.7")`
#### 1.2 `yaml` 파일 설정
```
spring:
  datasource:
    hikari:
      jdbc-url: jdbc:mariadb://localhost:3306/pika
      username: pika_app
      password: pika_password

  flyway:
    locations: classpath:/db/migration # migration 파일들이 위치하는 directory
    sql-migration-suffixes: ddl        # 파일 확장자
    baseline-on-migrate: true          # flyway_schema_history 테이블을 자동으로 생성할지 여부 
    baseline-version: 0                # 최초 버전 정보
```
#### 1.3 마이그레이션 파일
- `migration`: 데이터베이스에 일어나는 모든 행위
- ![image](https://user-images.githubusercontent.com/61215550/178890908-0822f58a-153b-411d-927e-a7b4cc545598.png)


|요소|설명|
|-----|-----|
|`Prefix`|V, U, R 중 하나 입력 / V(Version) U(Undo) R(Repeatable)|
|`Version`|버전 정보(정수, 소수, 날짜 가능)|
|`Seperator`|__(underscore 2개 사용)|
|`Description`|추가 설명|

- ![image](https://user-images.githubusercontent.com/61215550/178891435-fde9db86-c5f2-4b58-8d5d-c02345fca238.png)

### 2. 주의사항
> [참고자료](https://velog.io/@banjjoknim/DB-Migration-Tool#%EC%A3%BC%EC%9D%98%EC%82%AC%ED%95%AD)
- 기존에 존재하고 있던, 버전 관리에 반영된 `Script` 파일 >> 절대 수정, 삭제 ❌
- 새롭게 변경사항 발생 >> 새롭게 `Script` 추가 ✔
- 문제 발생 시 ㅠ,ㅠ >> `flyway_schema_history` 테이블 직접 변경
