---
layout: post
title: ERROR 1698 (28000):Access denied for user 'root'@'localhost' 해결하기
author: calm17ess
subtitle: ERROR 1698 (28000):Access denied for user 'root'@'localhost' Solve
categories: linux
banner:
  image: /assets/images/banners/posts_banners/mariadb.jpg
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  subheading_style: "color: gold"
tags: [linux, mariaDB, ERROR, mySQL]
---

## 발생한 컴퓨터

OS : Arch Linux<br>
Program : MariaDB-11.3.2-2<br>

## 에러 발생

mariadb를 접속했을 때 `ERROR 1698 (28000):Access denied for user 'root'@'localhost'` 발생.

```zsh
$ mysql -uroot
ERROR 1698 (28000):Access denied for user 'root'@'localhost'
```

## 에러 원인

비밀번호가 할당되지 않음(MariaDB 10.5 이상).

## 에러 해결

`set password`로 비밀번호를 할당해줌.

1. sudo 명령어로 mysql에 접속

```zsh
$ sudo mysql -uroot
```

```sql
    $ use mysql;
```

2. 비밀번호 설정

```sql
MariaDB [mysql] > set password for root@'localhost' = PASSWORD('자신이 원하는 비밀번호');
Query OK, 0 rows affected (0.* sec) => 성공했을 시 다음과 같은 메시지 출력
```

3. 접속 확인

```zsh
$ mysql -u root -p
mysql: Deprecated program name. It will be removed in a future release, use '/usr/bin/mariadb' instead
Enter password:
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 7
Server version: 11.3.2-MariaDB Arch Linux

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]>
```
