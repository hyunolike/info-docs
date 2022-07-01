## `Master-Slave` 서버
> [참고 자료](https://brunch.co.kr/@b30afb04c9f54dc/2)
- `DB` 서버의 과부하 및 운영을 위해 등장! ⭐
- 주인 <--> 노예 ✔
- 주인 `master` 
  - 메인 프로세스 담당
- 노예 `slave`
  - master 서버로부터 __복제된 데이터__ 받아 어시스트 같은 느낌 각종 기타 요청들 대응
- ![image](https://user-images.githubusercontent.com/61215550/176822598-afa8c8c0-8c6c-49a7-8e94-74c27354c99b.png)

### 복제 지연 해별 방법 ✔
![image](https://user-images.githubusercontent.com/61215550/176823502-0a2b787d-cb96-43c4-84b3-8eddedadda4b.png)
