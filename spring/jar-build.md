## `Jar` build
> [참고 자료](https://velog.io/@jwkim/spring-boot-build-jar)
- `Java Archieve` 약어 > `jar`
- java 어플리케이션을 배포, 동작할 수 있는 형태로 패키징(압축)한 파일 형태

### `bootJar`
- Spring Boot는 Plugin 통해 지원
- 실행가능한 jar을 빌드하는 테스크, 플러그인 포함
- 실행가능한 jar 만드는데 사용했던 `bootRepackage` >> Spring Boot 2.0에서 `bootJar`로 확장

#### 설정
- `build.gradle`에서 설정 추가
```groovy
bootJar {
	mainClass = 'com.example.ExampleApplication'
}
```
#### 빌드
- `./gradlew bootJar`
#### 실행
- `java -jar [파일명]`
- `./gradlew bootRun`

### ✔ `bootJar` vs `jar` | 2개 명령어 빌드 차이
> [참고 자료](https://earth-95.tistory.com/132#BootJar%EC%--%--%--%EC%-D%--%ED%--%B-%--%EC%--%-D%EC%--%B-%EB%--%-C%--jar%EC%--%--%--Jar%EC%--%--%--%EC%-D%--%ED%--%B-%--%EC%--%-D%EC%--%B-%EB%--%-C%--jar%EB%-A%--%--%EB%AC%B-%EC%--%--%EC%-D%B-%--%EB%-B%A-%EB%A-%BC%EA%B-%-C%-F)
- `bootJar`: `executable.jar(실행 가능한 jar)` 실행 바로 가능
- `jar`: 기본 `Manifest` 속성이 없다는 오류와 함께 실행되지 않음 ㅠ,ㅠ

#### ✔ `Jar`에 의해 생성된 jar
- `Jar`에 의해 생성된 jar >> `plain archive` 
  - 어플리케이션 실행에 필요한 모든 의존성을 포함하지 않고 소스코드의 클래스 파일과 리소스 파일만 포함
  - ⭐ 의존성을 제대로 포함하고 있지 않기 때문에 `java -jar` 명령어로 실행되지 않음 ㅠ,ㅠ

#### `BootJar`에 의해 생성된 jar
- `executable archive`
- 어플리케이션 실행에 필요한 모든 의존성을 함께 빌드
- `java -jar` 명령어로 실행 가능 😁
