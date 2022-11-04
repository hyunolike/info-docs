## `Docker` 이용해 `Oracle` 생성
> [참고자료](https://momobob.tistory.com/17) <br>
> [참고자료](https://jonghyeok-dev.tistory.com/56)

### `docker-compose.yml`
```yml
version: '3'
services:
  oracle11g:
    image: jaspeen/oracle-xe-11g
    container_name: oracle11g
    volumes:
      - ./oracle-data:/u01/app/oracle jaspeen/oracle-xe-11g
    ports:
      - 1521:1521
    environment:
      - ORACLE_ALLOW_REMOTE=true
```

### dbever
![image](https://user-images.githubusercontent.com/61215550/199864527-15a8a5e7-1c36-44d5-bcf8-9ff1ff423845.png)

### 결과
![image](https://user-images.githubusercontent.com/61215550/199864547-ee51ab72-7f02-4ee9-a37f-083c306de4a5.png)
