## docker `rm` / docker-compose `down` 
> [참고자료](https://stackoverflow.com/questions/56191955/whats-the-difference-between-down-and-rm-in-docker-docker-compose)
- 결론. 도커 컴포즈 사용시 `down` `up` 명령어 사용! ⭐
### docker rm
> [참고자료](https://www.lainyzine.com/ko/article/docker-rm-removing-docker-containers/)
- `docker rm [컨테이너]`
- `docker rm -f` >> 실행 중인 컨테이너 강제 삭제 명령어

### docker-compose down
- 모든 서비스 정지 + 종료

### (추가) 젠킨스 이용해 도커 컴포즈 재설치
- [참고자료](https://royleej9.tistory.com/entry/Jenkins-docker-docker-compose%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EC%97%AC-%EC%84%A4%EC%B9%98)
