## 도커 컴포즈로 다중 데이터베이스 생성 방법
- 단일 Docker 컨테이너의 여러 데이터베이스


```yml
version: '3'

volumes:
  db:
    driver: local

  services:
    db:
      image: mysql:5.7
      command: mysqld --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
      volumes:
        - ./docker/provision/mysql/init:/docker-entrypoint-initdb.d ⭐⭐
      environment:
        MYSQL_ROOT_PASSWORD: local
```
- `docker/provision/mysql/init/database.sql`
```sql
# create databases
CREATE DATABASE IF NOT EXISTS `primary`;
CREATE DATABASE IF NOT EXISTS `secondary`;

# create root user and grant rights
CREATE USER 'root'@'localhost' IDENTIFIED BY 'local';
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%';
```

