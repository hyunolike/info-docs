## AWS Elastic IP
> [참고자료](https://inpa.tistory.com/entry/AWS-%F0%9F%93%9A-%ED%83%84%EB%A0%A5%EC%A0%81-IP-Elastic-IP-EIP-%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80)
### Elastic IP
- 인터넷 > 고정적인 공인 IP 할당
- 인스턴스 연결할 수 있는 서비스


```
⭐DNS 서버 > 도메인 == IP주소

-> Elastic IP 주소 사용!! 
```


### 사용 이유
- EC2 > ENI(`Elastic Network Interface`) 따라오게 됨
  - ENI:  일종의 랜카드
  - 가상 이긴 하지만 랜카드 > MAC 주소와 보안그룹 연결되어 있어 `IP` 가지고 있다
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/66fc6c49-0532-438f-b882-a6e3e52a9487)
- 하지만!!
  - 인스턴스 Public IP > 고정된 IP 주소 아닌 > ✔유동적인 IP 주소
   - ![image](https://github.com/hyunolike/info-docs/assets/61215550/f3ab188f-8032-4e60-8253-d74a9a53bd43)
