# multibd -docker
This repository contains multiple database engines, such as SQL Server Express 2017, MySQL 8 and Oracle XE 11g

Clone the repo:
```sh
git clone https://github.com/ycharmx/multibd-docker/
```

Build the image:
```sh
docker build -t multibd .
```
Run the image (example):
```sh
docker run --rm -d \
 -e ACCEPT_EULA=Y -e SA_PASSWORD=[SQLServerPassord] \
 -e MYSQL_USER=hepc -e MYSQL_ROOT_PASSWORD=[MySQLPassword] \
 -e ORACLE_ALLOW_REMOTE=true \
 -p 3355:3306 \
 -p 1516:1521 \
 -p 1415:1433 \
 --name test-multibd \
multibd:latest
```

credentials

1. oracle
   - user: __system__
   - password: __oracle__
   - SID: __xe__ (no XE)
2. mysql
   - user: __root__
   - password: __MYSQL_ROOT_PASSWORD__ (MySQLPassword)
3. sql server
   - user: __sa__
   - password: __SA_PASSWORD__ (SqlServerPassword)
   
     - The sql password has to fullfil the SQL Server password requirements
     
      >  - The password does not contain the account name of the user.
      >  - The password is at least eight characters long.
      >  - The password contains characters from three of the following four categories:
      >  - Latin uppercase letters (A through Z)
      >  - Latin lowercase letters (a through z)
      >  - Base 10 digits (0 through 9)
      >  - Non-alphanumeric characters such as: exclamation point (!), dollar sign ($), number sign (#), or percent (%).
      >  - Passwords can be up to 128 characters long. Microsoft recommends using passwords that are as long and complex as possible.


I'am not the full author of this image

- mysql service based on: https://github.com/docker-library/mysql
- oracle xe 11g service based on: https://github.com/wnameless/docker-oracle-xe-11g
