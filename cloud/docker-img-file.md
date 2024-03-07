## docker 이미지 `파일` 로 저장 및 불러오기
> [참고자료](https://twpower.github.io/183-how-to-save-or-load-docker-image-file)
### 1. 도커 이미지를 파일로 저장
```shell
docker save [option] image(with tag) [image ...]

sudo docker save nginx:stable > nginx-stable-image.tar
sudo docker save nginx:stable -o nginx-stable-image.tar
```

### 2. 파일을 도커 이미지로 불러오기
```shell
docker load [option]

$ sudo docker load < nginx-stable-image.tar
$ sudo docker load -i nginx-stable-image.tar
```

