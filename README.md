# templates
This repo gathers frequently used template for development.

## Docker
### Docker MySQL
Create a mysql instance
```
docker run -d -p 13306:3306 --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -e MYSQL_DATABASE=mysqldb mysql:8.0.30
 ```

### Docker Oracle XE 11g
Refer to https://github.com/wnameless/docker-oracle-xe-11g
```
# pull image
docker pull wnameless/oracle-xe-11g-r2

# connect database remotely
docker run -d -p 49161:1521 -e ORACLE_ALLOW_REMOTE=true wnameless/oracle-xe-11g-r2

# default configuration
# hostname: localhost
# port: 49161
# sid: xe
# username: system
# password: oracle
```

## Spring
### application.yml
```
server:
  port: 8086
  servlet:
    context-path: /api
  ssl:
    enabled: false

spring:
  application:
    name: my-spring-app
  jpa:
    show-sql: true
    database-platform: org.hibernate.dialect.MySQL8Dialect
  datasource:
    url: jdbc:mysql://localhost:3306/my-database-name?createDatabaseIfNotExist=true
    driverClassName: com.mysql.cj.jdbc.Driver
    username: root
    password: [mysql-database-password]

mybatis:
  type-aliases-package: [my.spring.app.entity.package]
  mapper-locations: classpath*:mapper/*.xml
```
