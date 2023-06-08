## docker 모든 컨테이너와 이미지 삭제
> [참고자료](https://www.lainyzine.com/ko/article/how-to-remove-all-docker-contaniers-and-images/#%EC%8B%9C%EC%8A%A4%ED%85%9C-%EC%83%81%EC%9D%98-%EB%AA%A8%EB%93%A0-docker-%EC%BB%A8%ED%85%8C%EC%9D%B4%EB%84%88-%EC%82%AD%EC%A0%9C%ED%95%98%EA%B8%B0)

### `prune` 명령어
> [참고자료](https://www.lainyzine.com/ko/article/docker-prune-usage-remove-unused-docker-objects)



```shell
# 중지된 컨테이너 삭제
docker container prune

# dangling 상태의 이미지 삭제
# (dangling 이미지: 이미지 목록에서 태그가 없어 <none>으로 보이는 이미지)
docker image prune

# 사용되고 있지 않은 이미지 삭제
docker image purne -a

# system prune을 사용하면 중지된 컨테이너, dangling된 이미지, 사용하지 않는 볼륨, 사용하지 않는 네트워크를 한꺼번에 삭제해줍니다.
docker system prune
```
