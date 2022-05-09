## 여러 개의 docker-compose 파일 사용하기
> [영상 자료](https://www.youtube.com/watch?v=qaQn0cTLuO0)

### 실습
1. 3개의 `yml` 파일 생성
- ![image](https://user-images.githubusercontent.com/61215550/167367816-a8cd71bf-79e8-4c74-a486-86a89b6ca1f6.png)

2. `docker-compose -f a.yml -f b.yml -f c.yml`
- ![image](https://user-images.githubusercontent.com/61215550/167367912-6b2ab24a-a87b-46dc-bab7-b206bf7db4af.png)

3. 끝 ㅋㅋㅋㅋㅋㅋ간단

### Docker Compose 커멘드 사용법
> [참고 자료](https://www.daleseo.com/docker-compose/)
- `-f`
  - 기본적으로 커맨드가 실행하는 디렉토리에 있는 `docker-compose.yml` / `docker-compose.yml` 를 설정파일로 사용
