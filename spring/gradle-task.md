## `Gradle task`
> [참고 자료](https://blog.naver.com/sharplee7/221413629068)
- `task`: Gradle의 프로젝트 작업 단위 
  - `groovy` 언어로 작성
- 2가지 종류 존재 ✔
  - Gradle 내부에 미리 만들어져 있는 __내장 task들__
  - build.gradle 파일에 사용자 정의해 사용하는 __사용자 정의 task들__

### 사용자 정의 task 예시
```groovy
task [사용자 정의 테스크명]{
  // 내용
}
```
- `PROJECT_ROOT>gradle 테스크명`

### `Jar` 파일 생성
- `Tasks` > `build`
  - `bootjar` : jar파일 생성 - `[프로젝트명] + [build.gradle의 version].jar`
  - `clean` : 빌드했던 파일 삭제
