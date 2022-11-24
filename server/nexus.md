## nexus repository
> [참고자료](https://velog.io/@seokbin/Nexus-Repository-%EA%B5%AC%EC%B6%95-%ED%95%98%EA%B8%B0)
- ![image](https://user-images.githubusercontent.com/61215550/203686582-58d9a38d-34cf-413d-aadd-3619085f2649.png)
- 사내 비공개 저장소로 공유할 수 있는 `Private Repository` 
- 사내 보안 문제 해결 가능

### 사용 이유
##### 1. 적은 용량
- 저장소 >> 라이브러리 보관 >> 프로젝트마다 필요한 라이브러리를 버전 관리에 추가할 필요 없고 / 라이브러리에 대한 **메타데이터** 만 설정 >> 빌드할 때 내려받기에 적은 용량 차지
##### 2. 빠른 프로젝트 체크아웃 & 빌드
- 버전 관리 툴 이용 >> 프로젝트 체크아웃할 경우 >> 용량 적으므로 빨리 체크아웃할 수 있고 빌드 속도 빨라 ~~
##### 3. 라이브러리 버전 관리 용이
- **메타데이터** 기반!! 
- 라이브러리의 정보와 버전 관리하므로 라이브러리 자체의 버전 관리 쉬워
##### 4. 공유 및 협업 강화
- 저장소를 통해 컴포넌트 공유 가능!
- 개발자들끼리 손쉽게 산출물 공유 및 협업 가능!

### Nexus란?
- 현재 가장 인기 있는 `Repository Manager` >> Docker, Helm, Pypi, Mave 등 다양한 포맷 지원
- ![image](https://user-images.githubusercontent.com/61215550/203686334-e8de5bab-8300-4768-9b76-cddc4e684231.png)

### 설치 방법 - 자세한 구축 방법은 깃랩 참고 😛
> [참고자료](https://github.com/shankysharma86/nginx-nexus-docker)
- Docker
- ![image](https://user-images.githubusercontent.com/61215550/203686660-8bfbbc66-2e2a-4606-ae92-478d47489776.png)

#### `docker install`
```shell
mkdir /nexus-data
docker run --name nexus -d -p 5000:5000 -p 8081:8081 -v /nexus-data:/nexus-data -u root sonatype/nexus3 
```

#### `docker compose.yml`
```yml
version: '3'

services:
  nginx-nexusproxy:
    image: nginx-nexusproxy
    ports:
      - '443:443'
      - '6666:6666'
      - '7777:7777'
    links:
      - nexus-repo
    command: [ nginx, '-g', 'daemon off;' ]

  nexus-repo:
    image: sonatype/nexus3
    volumes:
      - 'nexus3-data:/nexus-data'

volumes:
  nexus3-data:
```
