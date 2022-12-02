## 리눅스 `chroot` `namespace` `cgroup`
> [참고자료](https://tomatohj.tistory.com/39)

### chroot
- 프로세스에 대해 새로운 root 디렉토리 지정하는 것
- ⭐즉, 프로세스에 대한 파일시스템 격리
- ![image](https://user-images.githubusercontent.com/61215550/205236170-b8d38bfd-b053-4e2c-a677-776683eb553c.png)

### namespace
- 프로세스 별 리소스 사용 분리하는 것
- ⭐즉, 프로세스에 대한 환경 격리(하드웨어 자원에 대한 분리 수행 안함!)
- ![image](https://user-images.githubusercontent.com/61215550/205236290-cd6c7eeb-bbeb-4fd5-bfb4-e62b47eeb432.png)

### cgroup
- 프로세스 별 가용 컴퓨팅 자원(메모리, cpu, device, disk i/o) 제어
- ![image](https://user-images.githubusercontent.com/61215550/205236472-936ad2a2-4033-4765-aeaf-c0b64a8882de.png)
