## 도커 컨테이너 이해
> [참고자료](https://tech.cloudmt.co.kr/2022/06/29/%EB%8F%84%EC%BB%A4%EC%99%80-%EC%BB%A8%ED%85%8C%EC%9D%B4%EB%84%88%EC%9D%98-%EC%9D%B4%ED%95%B4-3-3-docker-image-dockerfile-docker-compose/)

### 1. 도커 이미지
- 도커 사이트
  - 도커 공식 리포지토리 서비스
- `docker search [image]`
- `저장소`: 하나 이상의 컨테이너 이미지 저장하는 장소 
- `이미지`: 컨테이너의 기본이 되는 이미지 / 주로 이미지의 역할과 관련된 이름을 붙임 >> 생략 불가
  - 이미지 자체 사용 불가
  - 컨테이너 추가해서 할 수 있는 `패키지` 느낌 📡
- `태그`: 이미지의 버전 기록 
#### 1-1. images search
- `docker search [imgae] -f stars=10`
  - 인기 있는 도커 이미지 검색
### 2. 도커 이미지 관리
- `docker image pull`
- `docker image inspect [이미지명]` >> 이미지 상세 정보 확인 방법 ⭐
- `docker image tag [이미지 레포지토리]:태그(보통버전)`

### 3. 도커 이미지 비륻
```
FROM #운영체제 이미지

RUN  #실행할 명령어

CMD #컨테이너 명령 실행
```


- ![image](https://github.com/hyunolike/info-docs/assets/61215550/ace2a119-047e-45da-a9fd-da43846bd30b)
#### 3-1. ⭐`Dockerfile` - 레이어 최소한으로 사용하기!
- 운영체제 지정 >> 메모리 기반으로 동작 >> 컨테이너 용량 적게 하게끔 설정 필요
- ✔ `컨테이너`: 필요한 라이브러리 + 어플리케이션 모아 >> 별도의 서버처럼 해주는 거
  - 케익! >> 레이어 쌓아올림


```
#잘못된 예
FROM nginx
ENV Food “Chicken”
ENV Summer Cola Sea Vacation
ENV Time 1116

CMD ["/bin/bash"]

#레이어를 줄인 예

FROM nginx
ENV Food “Chicken” \
Summer Cola Sea Vacation \
ENV Time 1116
CMD ["/bin/bash"]
```
### 4. docker comopse 
```
version: ()
services: (docker container)
volumes: (docker volume)
networks: (docker network)
```



