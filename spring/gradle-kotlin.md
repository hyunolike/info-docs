## Gradle Kotlin DSL

### 1. 빌드 도구란?
- 소스코드를 실행가능한 애플리케이션 생성물을 자동으로 만드는 프로그램
- 빌드과정은 소스코드를 컴파일하고 >> 연결하고 >> 패키징하고 >> 실행가능한 형태로 가공!
#### 1.1 빌드 자동화 `Build automation`
1. 의존성 라이브러리 다운로드
2. 컴파일: 소스코드 >> 바이너리코드
3. 테스트 실행
4. 바이너리코드 패키징
5. 운영시스템 배포

#### 1.2 Gradle 짱ㅋㅋㅋㅋ
- 멀티 프로젝트 지원
- 래퍼 지원

### 2. Gradle 이란
-  유연함과 성능에 초점을 둔 오픈소스 빌드도구!

#### 2.1 멀티 프로젝트(혹은 모듈)
- Cross project configuration


```kotlin
import org.springframework.boot.gradle.tasks.bundling.BootJar

plugins {
    id("org.jetbrains.kotlin.jvm") version "1.3.21"
    id("org.jetbrains.kotlin.kapt") version "1.3.21"
    id("org.springframework.boot") version "2.1.4.RELEASE" apply false
    id("org.jetbrains.kotlin.plugin.spring") version "1.3.21" apply false
    id("com.gorylenko.gradle-git-properties") version "1.5.1" apply false
}

allprojects {
    repositories {
        jcenter()
    }
}

subprojects {
    apply(plugin = "kotlin")
    apply(plugin = "kotlin-kapt")
    apply(plugin = "org.springframework.boot")
    apply(plugin = "io.spring.dependency-management")
    apply(plugin = "org.jetbrains.kotlin.plugin.spring")
    apply(plugin = "com.gorylenko.gradle-git-properties")

    group = "io.honeymon.boot"
    version = "1.0.0"

    dependencies {
        compile("com.fasterxml.jackson.module:jackson-module-kotlin")
        compile("org.jetbrains.kotlin:kotlin-reflect")
        compile("org.jetbrains.kotlin:kotlin-stdlib-jdk8")
        compile("org.springframework.boot:spring-boot-starter-logging")

        /**
         * @see <a href="https://kotlinlang.org/docs/reference/kapt.html">Annotation Processing with Kotlin</a>
         */
        kapt("org.springframework.boot:spring-boot-configuration-processor")
        compileOnly("org.springframework.boot:spring-boot-configuration-processor")

        testCompile("org.springframework.boot:spring-boot-starter-test")
    }

    tasks {
        compileKotlin {
            kotlinOptions {
                freeCompilerArgs = listOf("-Xjsr305=strict")
                jvmTarget = "1.8"
            }
            dependsOn(processResources) // kotlin 에서 ConfigurationProperties
        }

        compileTestKotlin {
            kotlinOptions {
                freeCompilerArgs = listOf("-Xjsr305=strict")
                jvmTarget = "1.8"
            }
        }
    }
}

project("bootiful-core") {
    dependencies {
        compile("org.springframework.boot:spring-boot-starter-data-jpa")

        runtimeOnly("com.h2database:h2")
    }

    val jar: Jar by tasks
    val bootJar: BootJar by tasks

    bootJar.enabled = false
    jar.enabled = true
}

project(":bootiful-sbadmin") {
    dependencies {
        compile(project(":bootiful-core"))

        compile("de.codecentric:spring-boot-admin-starter-server:2.1.4")
        compile("org.springframework.boot:spring-boot-starter-web")
    }
}

project("bootiful-api") {
    dependencies {
        compile(project(":bootiful-core"))

        compile("de.codecentric:spring-boot-admin-starter-client:2.1.4")
        compile("org.springframework.boot:spring-boot-starter-web")
        compile("org.springframework.boot:spring-boot-starter-security")
        compile("org.springframework.boot:spring-boot-starter-actuator")

        runtime("org.springframework.boot:spring-boot-devtools")
    }
}
```

#### 2.2 래퍼 `Wrapper`
- 빌드도구 래퍼 제공되기 전
  - 각 개발자가 자신의 환경에 빌드도구를 설치하여 실행환경설정을 하고 관리해야 됬음...ㅠ,ㅠ 
  - 각 개발자마다 빌드도구 버전이 다른 경우 실행되지 않는 문제점 발견! >> 이를 해결하고자 


|종류|프로그램|
|----|-------|
|`Java`|SDKMan|
|`Mac Book`|Homebrew|
|`Linux`|APT / RPM|


- 위와 같이 설치된 패키지 관리!!!
- ✔ 빌드도구 래퍼: 빌드도구를 실행할 수 있는 jar파일과 이를 실행할 수 있는 스크립트를 함께 등록하여 관리하는 방식
  - 래퍼를 사용하면서 같은 프로젝트 작업자 로컬에 빌드도구를 설치하는 번거로움 사라짐 
  - 레퍼 버전을 업그레이드 >> 변경사항 커밋 후 >> 원격저장소에 푸시하면 이후에는 팀원들에게 업그레이드된 래퍼 공유 
  - 이는 젠킨스에서 빌드 작업을 처리할 때도 유용



```
.
├── gradle
│   └── wrapper
│       ├── gradle-wrapper.jar // 그레이들 래퍼 jar 😛
│       └── gradle-wrapper.properties // 그레이들 래퍼 버전 및 실행환경 기록 😛
├── gradlew // Unix 계열에서 실행가능한 스크립트
└── gradlew.bat // 윈도우에서 실행가능한 스크립트


// ./gradlew wrapper --gradle-version=
$ ./gradlew wrapper --gradle-version=5.4

// 이 글을 쓰고 있는 사이에 5.4.1 버전이 출시(2019-04-26)했다.
// 5.4 부터 JDK 12 지원한다. 내 프로젝트는 JDK 8에서 머물러 있는데...
```

### 3. ⭐ Gradle Kotlin DSL
- `Groovy DSL` `Kotlin DSL` >> 확장자명으로 구분!
- 멀티 프로젝트 빌드할 때는 각 모듈별로 각각 Groovy DSL / Kotlin DSL 작성하여 사용 가능
- ![image](https://user-images.githubusercontent.com/61215550/188449012-d2b74e8a-c1ae-4912-96ca-3ace5aa38988.png)


```groovy
def spockVersion = '1.2-groovy-2.5'

dependencies {
  😛 여기서 testComoplie, testImplementation 과 같은 옵션은 >> 빌드과정에서 배포본에 포함되지 않음!! 
  testImplementation 'org.codehaus.groovy:groovy'
  testImplementation "org.codehaus.groovy:groovy-test"
  testImplementation "org.spockframework:spock-core:$spockVersion"
  testImplementation("org.spockframework:spock-spring:$spockVersion")  
}
```


|Groovy|Kotlin|
|-----|-------|
|자유로움 / 작성자마다 각기 다른 형태로 작성 가능 ㅠ,ㅠ|제약 / 여러 사람 함께 사용하기 좋아~(주관적 의견이야 ㅋㅋㅋ)|


- ⭐Kotlin DSL 이득
  - 코드 자동완성
  - 오류코드 강조
  - 빠른 문서보기 가능
  - 리팩터링
- ![image](https://user-images.githubusercontent.com/61215550/188449720-6f58360b-d8d2-4c53-abc3-91c5d954997a.png)
