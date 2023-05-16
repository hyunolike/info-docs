## Logrotate (Linux)
> [참고자료](https://server-talk.tistory.com/271)

### Logrotate란
- 로그 관리 설정하는 기능
- 로그 저장 및 관리하는 도구
  - 기본적으로 `cron` 데몬 이용 >> logrotate 실행
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/25ebe24b-0596-43f0-b6e4-bcfcd06ff0b7)

### `/etc/logrotate.conf` 설정
#### 1. 회전 주기
```
# rotate log files weekly
weekly

# 회전 주기
yearly: 매년
monthly: 매월
weekly: 매주 
daily: 매일
```
#### 2. 로그파일 개수
```
# keep 4 weeks worth of backlogs
rotate 5
```
#### 3. 새로운 로그파일 생성여부
```
# create new (empty) log files after rotating old ones
create

# 생성여부
create : 로그파일 생성
empty: 로그파일 생성 안함
```
#### 4. 파일명 날짜 부여
```
# use date as a suffix of the rotated file
dateext ...
```
### ✔ 예제
- ![image](https://github.com/hyunolike/info-docs/assets/61215550/5a7af57c-12c3-4e05-b45d-db53a7921a2c)
```
1. 압축에 대해 명시적으로 써져있지 않은 모든 로그는 압축한다.

2. (1) /var/log/messages에 대해 매주마다 실행한다.

    (2) 최대 5개까지 보관가능하다(최대 5주 보관), 

    (3) logrotate 실행 후 /usr/bin/killall -HUP syslogd 명령을 실행한다.

3. (1) /var/log/httpd/access.log와 /var/log/httpd/error.log에 대한 설정이다.

    (2) size는 100k이상일 때 logrotate를 실행한다.

    (3) 최대 5개까지 보관가능하다.

    (4) 로그처리 중 발생한 오류는 www@my.org로 보낸다. 

    (5) 다음에 나오는 스크립트는 공유한다.

    (6) 2가지의 로그파일이 모두 처리된 후 /usr/bin/killall -HUP httpd를 실행한다.

4. (1) /var/log/news/에 있는 모든 로그파일에 대한 설정이다. 

    (2) 매달마다 실행하며 최대 2개까지 보관가능하다.

    (3) 오래된 로그는 /var/log/news/old 디렉토리에 옮긴다.

    (4) 로그파일이 없더라도 에러처리하지 않는다. 

    (5) logrotate 실행 후 kill -HUP cat /var/run/inn.pid  명령을 실행한다.

    (6) 해당 로그들은 압축하지 않는다.
```


