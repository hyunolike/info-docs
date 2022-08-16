## Logging 간단 설정 `logback`
> [참고자료](https://gofnrk.tistory.com/107)
- 작은 규모: `application.yml` 파일 설정
- 큰 규모(세부적 설정 필요): `logback.xml` 


```yml
logging:
  file:
    path: /Users/hong/Logs/kotlin-spring
    max-size: 500MB
    max-history: 10
  level:
    root: info
    me.hong.kotlinspring: debug
```
