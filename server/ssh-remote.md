## `SSH` 원격 명령어 실행 - ssh 이용해 암호없이 원격 서버 명령어 실행하자
> [참고자료](https://m.blog.naver.com/wideeyed/222127416155)
- ![image](https://user-images.githubusercontent.com/61215550/203184492-526b91ba-06c0-4e70-8e5f-4b577db1f9ba.png)
### 순서
1. 로컬서버(여기서 명령어 칠꺼야)  SSH Key 발급
2. 원격서버 구성 및 발급한 SSH Key 공개키 복사
3. 로컬서버 >> SSH 이용해 원격 명령어 호출


```shell
ssh -p 9001 user2@127.0.0.1 "top -b -d1 -n1|grep -i 'Cpu(s)'|head -c21|cut -d ' ' -f3|cut -d '%' -f1"
```
