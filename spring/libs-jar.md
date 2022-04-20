## springboot 외부 라이브러리 jar 파일 추가 방법
- ![image](https://user-images.githubusercontent.com/61215550/164167899-e0b98560-e14f-4e5d-904c-a90a4258cc01.png)
1. 먼저 위의 사진처럼 폴더 안에 라이브러리 넣은 후!!
2. 아래 코드를 사용해 추가하자

`한 개의 파일 넣는 방법`
```java 
dependencies {
  implementation files('libs/라이브러리.jar')
}
```


`디렉토리에 위치한 모든 라이브러리의 의준성을 추가하는 방법
```java
dependencies {
   compile fileTree(dir: 'libs', include: ['*.jar'])
}
```
