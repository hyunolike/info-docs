## `package.json` `package-lock.json`
> [참고자료](https://velog.io/@songyouhyun/Package.json%EA%B3%BC-Package-lock.json%EC%9D%98-%EC%B0%A8%EC%9D%B4)
- ✔ `package.json` 버전 정보 저장 시 >> version range 사용!
   - 일정 버전 이상 미만 범위 지정하는 거
- (참고) 버전 오류 발생 시 해결방법
  - ![image](https://user-images.githubusercontent.com/61215550/206962015-d7f337b9-8e77-44aa-aece-76fb0a6275b3.png)
### 차이
> ⭐ `package-lock.json` 파일 있는 경우 이걸 토대로 `node_modules` 폴더 생성!
- `package.json`: 틸드(~)로 버전 범위 명시
- `package-lock.json`: 버전명 정확히 명시
  - `package.json` 으로 부족한 정보 도와주는 파일
  - 반드시 소스 저장소에 커밋 요망
