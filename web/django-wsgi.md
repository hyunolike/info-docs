## Django - WSGI
> [참고자료](https://jay-ji.tistory.com/66)
- WSGI
    - 서버 / 게이트웨이 / 애플리케이션 / 프레임워크 양단
    - WSGI 미들웨어 (서버 관점 > 애플리케이션 / 애플리케이션 관점 > 서버)


```
HTTP req > Web Server > WSGI Server(미들웨어) > Django(WSGI 지원 Web Application)
```


- gunicorn
    - Python WSGI HTTP Server
### 구조
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/8cdd0a16-39cd-4de5-a7f1-7f5c2f8aad89)
