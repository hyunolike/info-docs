## linux `curl`
> [참고자료](https://jjeongil.tistory.com/1313)
- 💡대부분의 리눅스 배포 환경에는 curl 미리 설치되어있음
  - 🙄도커 컨테이너로 생성된 리눅스 서버에서는 `curl` 별도 설치 요망

### 설치 방법
```shell
sudo apt update
sudo apt install curl
```

### 사용 방법
```shell
curl [options] [URL...]
```

### 출력을 파일에 저장하자
- ✔ `-o` `-O`
  - Lowercase `-o`은 미리 정의된 파일 이름을 사용해 파일 저장!


```shell
curl -o vue-v2.6.10.js https://cdn.jsdelivr.net/npm/vue/dist/vue.js
```
