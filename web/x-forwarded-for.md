## X-Forwarded-For
> [참고자료](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Forwarded-For)

- 프록시 서버 통해 웹 서버에 연결하는 클라이언트의 원래 IP 주소 식별하기 위한 사실상 표준 헤더



```
클라이언트 IP --> Proxy 서버 및 장비 --> 웹 서버
```

 
### `Web Server` - Nginx 에서 사용 시 따로 설정 필요 📗
- `-with-http_realip_module` 옵션 필요


```
http {
set_real_ip_from 127.0.0.1; # proxy/L4 서버 IP
real_ip_header X-Forwarded-For; #proxy/L4 가 실제 IP 를 설정하는 HTTP Header
```
