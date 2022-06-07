## `Windows` - ICACLS
> [참고 자료](https://cloudest.oopy.io/posting/046)
- `ICACLS`: 윈도우에서 권한, 상속, ACL과 같은 항목들을 설정할 수 있는 명령어
- 파일의 소유권: `takeown` 명령어
- 파일 혹은 폴더의 권한: `ICACLS` 명령어

### `Grant` 
```shell
ICACLS "[경로]" /grant[:r] [사용자or그룹]:[권한]

icacls "\\172.16.97.238\share\10. Sharing Folder\00. From SAS" /inheritance:d /t
```

### 참고 옵션 리스트
> [공식 홈페이지](https://docs.microsoft.com/ko-kr/windows-server/administration/windows-commands/icacls)
- `[권한]` 
  - F: 모든 권한
  - M: 엑세스 수정
  - RX: 엑세스 읽기 및 실행
  - R: 읽기 전용
  - W: 쓰기 전용 엑세스
- 특정 `[권한]`은 괄호 안  쉼표로 구분 (ex. `[폴더]:(R,W,D)`)
- 상속관련 `[권한]` 옵션은 디렉토리에만 적용
- grant와 자주 사용하는 옵션
  - /T: 지정된 디렉터리 하위 모든 파일들에게 이 작업 수행
  - /C: 오류가 있어도 작업 진행(오류 메시지 표시)
  - /Q: 성공 메시지 표시X
- ![image](https://user-images.githubusercontent.com/61215550/172288694-ba721a86-072a-42a5-b422-a29c682ec646.png)


### 추가 실제 코드 분석
- ![image](https://user-images.githubusercontent.com/61215550/172288890-c5840e26-9080-4e7f-856e-7c749b97e10c.png)
