## Docker logs
> [참고자료](https://velog.io/@cckn/TIL-docker-logs%EC%9D%98-%EC%98%B5%EC%85%98%EA%B3%BC-%EC%82%AC%EC%9A%A9-%EC%8B%9C%EB%82%98%EB%A6%AC%EC%98%A4)
- `docker logs` >> 컨테이너의 로그를 조회할 수 있는 명령어
- 명령어: `docker logs [OPTIONS] CONTAINER`
  - `OPTION` 부여 시, 원하는 대로 볼 수 있음

```shell
docker logs -f [컨테이너 이름]
```

### 사용 예시
#### 1. 마지막에 찍히는 10개의 로그만 보고 싶다
- `docker logs --tail 10 <CONTAINER>`

#### 2. 지금부터 생성되는 로그도 보고 싶다
- `docker logs -f <CONTAINER>`
  - `-f` 옵션: 로그 출력하고 프로세스 종료하는게 아닌 계속해서 로그 추적! 📌

#### 3. 기존의 로그 무시하고 새로 생성되는 로그만 보려면
- `docker logs -f --tail 0 <CONTAINER>`

#### 4. 특정 메시지가 들어간 로그만 보고 싶다면
- `docker logs test | grep :20`
  - ✔ `grep` 이후에 검색하고자 하는 텍스트 넣어주면 됨!
