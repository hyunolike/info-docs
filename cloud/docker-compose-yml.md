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
