## `pubxml` 파일 형식
> [참고자료](https://points.tistory.com/101)

- ⭐ dot net 배포 > `Web Deploy(MS Deploy)`
- Web Deploy 도구에 사용되는 파일

### 단계
1.  Publish Profile 생성
2.  배포하지 않을 파일설정
  - `<Content />`
  - `<MsDeploySkipRules />`
3. 배포에 포함할 파일설정
  - `<Content />`
  - `<ResolvedFileToPublish />`
  
