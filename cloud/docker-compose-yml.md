## Docker Compose yml 파일 
> [참고 자료](https://docs.docker.com/compose/compose-file/#external-1)
- 도커 애플리케이션의 서비스, 네트워크 및 볼륨 정의하는 파일
### Compose Application Model
- 컨테이너 기반 애플리케잉션 정의 가능
- 응용 프로그램의 컴퓨팅 구성 요소 >> 서비스 ✔
- 서비스는 __네트워크__ 를 통해 서로 통신!
- 서비스는 영구 데이터 >> 볼륨 ✔ 저장 + 공유
- 일부 서비스는 런타임 또는 플랫폼에 종속된 구성 데이터 필요 >> `Configs` 정의
  - 볼륨과 유사하지만 추상화된 별개의 플랫폼 리소스 및 서비스 포함
- `Secret` >> 보안 고려 사항 없이 노출되어서는 안되는 민감한 데이터에 대한 구성 데이터의 특징

### 예시
```
(External user) --> 443 [frontend network]
                            |
                  +--------------------+
                  |  frontend service  |...ro...<HTTP configuration>
                  |      "webapp"      |...ro...<server certificate> #secured
                  +--------------------+
                            |
                        [backend network]
                            |
                  +--------------------+
                  |  backend service   |  r+w   ___________________
                  |     "database"     |=======( persistent volume )
                  +--------------------+        \_________________/
```

```yml
services:
  frontend:
    image: awesome/webapp
    ports:
      - "443:8043"
    networks:
      - front-tier
      - back-tier
    configs:
      - httpd-config
    secrets:
      - server-certificate

  backend:
    image: awesome/database
    volumes:
      - db-data:/etc/data
    networks:
      - back-tier

volumes:
  db-data:
    driver: flocker
    driver_opts:
      size: "10GiB"

configs:
  httpd-config:
    external: true

secrets:
  server-certificate:
    external: true

networks:
  # The presence of these objects is sufficient to define them
  front-tier: {}
  back-tier: {}
```

### 작성 및 활용
- 기본적으로 현재 디렉토리 또는 상위 디렉토리에서 `docker-compose.yml` 파일 찾아 컨테이너 생성 
- `-f` 옵션을 이용해 위치와 이름 지정 가능

#### 1. 버전 정의
> [최신 버전](https://docs.docker.com/compose/compose-file/compose-versioning/)
- 도커 컴포즈 버전은 도커 엔진 버전에 의존성이 있기에 가능하면 최신 버전 사용

#### 2. 서비스 정의
- `image`: 서비스의 컨테이너를 생성할 때 쓰일 이미지의 이름 설정
  - 이미지 존재하지 않을 경우 저장소에서 자동으로 내려받음
- `links`: `--link`와 동일 / 다른 서비스에 서비스명만으로 접근할 수 있도록 설정
- `environment`: `--env` `-e` 옵션과 동일 / 컨테이너 내부에서 사용할 환경변수 설정
- `command`: 명령어의 마지막에 붙는 커맨드와 같으며, 컨테이너가 수행될 때 수행할 명령어 설정
- `depends_on`: 특정 컨테이너에 대한 의존 관계 / 이 항목에 명시된 컨테이너가 먼저 실행되고 해당 컨테이너 실행
  - ⭐db 의존시 mssql과 같은 db는 시작이 느려 db가 꺼진 상태에서 실행되는 경우 있음.
  - 이를 방지하고자 2개의 도커 컴포즈 파일을 구성해서 서로 의존되지 않게 구성하면 된다.
- `ports`: `-p` 옵션과 같음 / 서비스의 컨테이너를 개방할 포트 설정
- `build`: 도커파일에서 이미지를 빌드해 서비스의 컨테이너를 생성하도록 설정
- `extends`: 다른 YAML 파일이나 현재 YAML 파일에서 서비스 속성 상속

#### 3. 네트워크 정의
- `driver`: 서비스의 컨테이너가 브리지 네트워크가 아닌 다른 네트워크 사용하도록 설정
- `ipam`: IPAM(IP Address Manager)를 위해 사용할 수 있는 옵션으로 subnet, ip 범위 등을 설정
- `external`: YAML 파일을 통해 프로젝트 생성할 때마다 네트워크를 생성하는 것이 아닌 __기존의 네트워크__ 사용하도록 설정 ✌
- ✔ 네트워크 항목을 정의하지 않으면, 도커 컴포즈는 프로젝트별로 브리지 타입의 네트워크 생성
  - 생성된 네트워크 이름 `[프로젝트 명]_default` 

#### 4. 볼륨 정의
- `driver`: 볼륨 생성할 때 사용될 드라이버 설정 / 어떠한 설정도 하지 않으면 local로 설정되며 사용하는 드라이버에 따라 변경
- `external`: 프로젝트 생성할 때마다 볼륨을 매번 생성하지 않고 __기존 볼륨__ 을 사용할 수 있도록  설정 ✌

#### 5. 파일 검증
- `docker-compose config` 명령어 사용
  - 오타나 파일 포맷이 적절한지 등에 대한 검사 진행
  - 기본적으로 현재 디렉토리의 파일 검사 / `docker-compose -f [yml파일 경로] config` 로 변경 가능
### 도커 명령어
- `docker-compose up -d` 도커 컴포즈 컨테이너들 백그라운드 띄우기
- `docker-compose up`
- `docker-compose down`
- `docker-compose restart`
- `docker-compose logs -f` 로그 계속해서 읽기
- `docker-compose ps`
- `docker-compose config`
- `docker-compose -f /app/docker-compose.yml up` 
- `docker-compose -f docker-compose.yml -f docker-compse-test.yml up` 여러 개의 도커 컴포즈 설정 파일 사용 가능 / 나중에 나오는 설정보다 우선으로 적용

