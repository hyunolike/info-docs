## VPN 연결된 서버 원격으로 접속 방법
> [참고자료](https://www.lainyzine.com/ko/article/how-to-connect-to-linux-server-with-ssh-on-windows-10/)

### 현재 상황
- source server: `windows server`
- target server: `linux` 
- 연결: vpn(ssh)

### 접속 방법
#### 1. openssh 설치
- 다른 자료 참고

#### 2. openssh 섥치 확인 및 실행
#### 3. openssh 명령어 실행
##### 3-1. 원격 접속 `source server` --> `target server`
```shell
$ ssh [USER]@[HOSTNAME] -p [PORT]
```

#### 3-2. 파일 복사 `source server` --> `target server`
```shell
$ scp [파일경로] -P [포트번호] [사용자]@[IP주소]:[원격파일경로] 
```
