## 배포 환경별 설정하기
> [참고 자료](https://pjh3749.tistory.com/262)


- ⭐여러 서버별로 배포할 때 각자 다른 설정으로 배포
- 예시> __개발용 서버__ = 개발 설정 / __운영 서버__ = 운영 설정 📌 각기 다르게 설정!!
![image](https://user-images.githubusercontent.com/61215550/166412181-33b7f5cc-34eb-4d14-add3-6c4d7083f5e8.png)

### ✔서버별 배포 환경 설정
- 배포 진행시 환경 변수 삽입 > 운영 환경마다 다른 설정파일 읽게 하자
- 최상위 부모 설정 파일 `application.yml`
- ![image](https://user-images.githubusercontent.com/61215550/166412472-ac60fcae-81bc-40c4-94ae-8039d394f413.png)
- `yml` 파일인 경우 하나의 파일에 설정 가능 ✔

### ✔ `YML` 로컬환경/개발환경/운영환경
> [참고 자료](https://yhmane.tistory.com/74)

#### 1. `application.yml` 설정
```YML
# profiles 값 할당 전
server:
    port: 18080
---
# profiles value 할당 (방법1)
# java -jar 파일명.jar --spring.profiles.active=profiles값 (택1)
# java -Dspring.profiles.active=profiles값 -jar 파일명.jar (택2)
spring:
    profiles: local
server:
    port: 8080
---
# profiles value 할당 (방법2)
# Edit Configurations > Run/Debug Configurations > Active Profiles 값 할당
spring:
    profiles: dev
server:
    port: 8081
---
spring:
    profiles: real
server:
    port: 80
```
- ⭐profiles 값 설정하지 않으면 최상단 port 적용!!

#### 2. `profiles` 설정
```
# java -jar 파일명.jar --spring.profiles.active=profiles값 (택1)
# java -Dspring.profiles.active=profiles값 -jar 파일명.jar (택2)
```
- ![image](https://user-images.githubusercontent.com/61215550/166413533-ebfdf6fa-2b28-4585-8bf6-8ca43a79cb3e.png)
