## `VM` `Container`
> [참고자료](https://daaa0555.tistory.com/464)
- ![image](https://user-images.githubusercontent.com/61215550/205229900-d4de6699-42f9-4621-8601-cb510eeddaf7.png)
### 1. VM
- 공통적으로 하나의 서버! 한 서버에는 어떤 운영체제 있든 HOST OS 올라감! 
- 호스트OS >> VM 가상화 시켜주는 하이퍼바이저(`virtual box, Xen, KVM, VMware`)
- 하이퍼바이저 사용해 원하는 운영체제 >> `GuestOS` 올려 여러 VM 생성 가능
- ⭐ 하나의 OS를 독립적으로 가지고 있는 것처럼 사용 가능!

### 2. 컨테이너
- `os` 에 의해 컨테이너 가상화 시켜주는 소프트웨어 `docker` `rkt` `LXC` >> 도커 가장 많이 사용

### 3. VM, 컨테이너 차이
> ⭐ 쿠버네티스 >> 여러 컨테이너들 묶기 >> 하나의 배포 단위 <br> 
> 컨테이너 >> 시스템을 모듈별로 쪼개서 개발했을 떄 큰 효과!
- ![image](https://user-images.githubusercontent.com/61215550/205233294-b649cf43-ca28-44ff-9055-2dd4d63071d4.png)
