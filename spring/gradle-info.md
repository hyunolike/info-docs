## `Gradle` 
- ![image](https://user-images.githubusercontent.com/61215550/167990775-6418c185-cc1b-4805-96fe-ab85f86aac9b.png)
- `Gradle` = core(본체) + plugin ✔
- 빌드 기능은 Core가 아닌 __Plugin__ 으로 구현

### `build.gradle` > gradle의 init task에 의해 생성되는 파일
- 기본 파일 `groovy` 작성
- groovy 그대로 사용이 아닌 gradle에서 사용하기 쉽게 만든 것 (`DSL`)
```groovy
buildscript {
    ext {
        springBootVersion = '2.1.7.RELEASE'
    }
    repositories {
        mavenCentral()
        jcenter()
    }
    dependencies {
        classpath("org.springframework.boot:spring-boot-gradle-plugin:${springBootVersion}")
    }
}

apply plugin: 'java'
apply plugin: 'eclipse'
apply plugin: 'org.springframework.boot'
apply plugin: 'io.spring.dependency-management'

group 'com.jojoldu.book'
version '1.0.1-SNAPSHOT'
sourceCompatibility = 1.8

repositories {
    mavenCentral()
}

dependencies {
    compile('org.springframework.boot:spring-boot-starter-web')
    testCompile('org.springframework.boot:spring-boot-starter-test')
}
```

#### buildscript
- 빌드 스크립트 자체를 빌드하는 과정에서 필요한 외부 라이브러리에 클래스패스에 추가하는 기능

#### repositories
- 저장소 설정

#### ext
- 그 인자를 buildScript에서 전역변수로 사용하기 위해 사용되는 메서드

#### dependencies
- 이행적 의존성이 아닌 일반 파일로 저장된 외부 라이브러리 지원
- 빌드 스크립트에서 직접 의존성 지정

#### apply plugin
- 플러그인 추가

#### ...
