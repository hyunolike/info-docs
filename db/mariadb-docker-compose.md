## 마리아 디비 + `docker-compose` 만들어버리자!
> [참고자료](https://velog.io/@shin6949/mariaDB-Docker-Container-%ED%99%98%EA%B2%BD%EC%84%A4%EC%A0%95)
- ✔ 도커 명령어로 배포하는 방법 있지만 !!! >> 명령어 길어지고 각 옵션 뜻하는게 무엇인지 헷갈림
- 깔끔하게 `Docker-compose` 사용하자! ⭐

### ⭐ 우리나라에서 DB 구성시 고려할 부분 2가지
- 기본 `charset` >> utf8 / utf8mb4 등으로 설정해 `한글` 저장할 수 있도록 설정
- `Timezone` >> GMT+9 설정 >> `now()` 등의 쿼리 사용 시 문제 없도록 해야됨!

### Docker Compose
```yml
version: '3.1'

services:
  mariadb:
    container_name: MMIS_secret_chat_DB
    image: mariadb:latest
    restart: always
    ports: 
      # host 3366 port connect
      - 3366:3306
    volumes:
      # DB 데이터 저장 디렉터리
      - ./data:/var/lib/mysql
      # 설정 파일 저장될 위치
      - ./config:/etc/mysql/conf.d
    environment:
      - "MYSQL_ROOT_PASSWORD=1111"
      - "TZ=Asia/Seoul"
    command:
      # 위 명령어를 사용하지 않으면, 일부 설정이 latin으로 설정
      - --character-set-server=utf8mb4
      - --collation-server=utf8mb4_unicode_ci
```

### 설정별 설명
#### Image 버전
- 서버 버전 확인
#### 포트 노출 설정
- 외부 통신 없이 컨테이너들 사이에서 통신 시  >> `expose` 설정!!
- 외부 통신시 바인딩할 >> `ports` 설정!!! 
#### 볼륨 설정
- ✔ 크게 2가지
  - `data`: mariaDB의 데이터 저장되는 디렉터리와 연결 / 컨테이너 재시작하여도 데이터 초기화하지 않는다!!
  - `config`: charset >> `UTF8MB4` 설정하기 위한 conf.d 파일들 연결시켜주기 위해 설정
#### 환경변수 설정
- 비번, 시간대
