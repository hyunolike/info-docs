## `docker network` 이용해 네트워크 공유
> [참고 자료](https://ooeunz.tistory.com/83)

- docker network : 실행된 각각의 컨테이너끼리 연결하기 위한 논리적인 네트워크
  - 각각의 컨테이너의 ip 지정해주거나 name만으로 손쉽게 컨테이너 연결한다는 장점
  - 아웃바운드 포트를 오픈하지 않는 이상 내부적으로만 통신 가능 
  - ![image](https://user-images.githubusercontent.com/61215550/167321338-8c18ae4b-8820-4332-9e09-d2aeeffef726.png)

### 실습
1. 도커 컨테이너끼리 네트워크 만들고, 그 네트워크 안에 속한 컨테이너끼리 private 통신 할 수 있도록 자동 연결
  - `docker network create <네트워크 이름>`
2. 이미지 생성된 전제하에 진행
  - `docker run -d --name <컨테이너 이름> -p <포트 번호> --network <네트워크 이름> <이미지 이름>`

