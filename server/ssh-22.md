## 리눅스 ssh 다른 포트로 접속 -p
> [참고자료](https://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_ssh_%EB%8B%A4%EB%A5%B8_%ED%8F%AC%ED%8A%B8%EB%A1%9C_%EC%A0%91%EC%86%8D_-p)

### 예시 
#### 1. ssh 서버 측의 포트가 기본포트 22번이 아니고 1234번인 경우
```sh
[root@mylinux ~]# ssh testuser@135.79.246.80
ssh: connect to host 135.79.246.80 port 22: Connection refused
```

#### 2. 아래처럼 해결!
```sh
[root@mylinux ~]# ssh testuser@135.79.246.80 -p1234
testuser@135.79.246.80's password:
```
