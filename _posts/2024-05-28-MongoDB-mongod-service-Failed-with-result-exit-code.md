---
layout: post
title: "mongod.service: Failed with result 'exit-code'. 해결하기"
author: calm17ess
subtitle: "How to solve mongod.service: Failed with result 'exit-code'."
categories: MongoDB
banner:
  image: /assets/images/banners/posts_banners/mongodb.png
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  subheading_style: "color: gold"
tags: [linux, arch, mongodb, mongod.service, exit-code]
---

## 발생한 컴퓨터

OS : Arch Linux<br>
Program : mongodb-7.0.9.1<br>

## 에러 발생

MongoDB를 실행시키고 상태를 확인하기위해 `sudo systemctl status mongodb` 를 했을 때 에러확인. <br>
MongoDB 실행 오류

```zsh
mongodb.service - MongoDB Database Server
     Loaded: loaded (/usr/lib/systemd/system/mongodb.service; enabled; preset: disabled)
     Active: failed (Result: exit-code) since Tue 2024-05-28 06:12:56 KST; 13s ago
   Duration: 50ms
       Docs: https://docs.mongodb.org/manual
    Process: 24895 ExecStart=/usr/bin/mongod --config /etc/mongodb.conf (code=exited, status=14)
   Main PID: 24895 (code=exited, status=14)
        CPU: 48ms

 5월 28 06:12:56 Arch systemd[1]: Started MongoDB Database Server.
 5월 28 06:12:56 Arch mongod[24895]: {"t":{"$date":"2024-05-27T21:12:56.324Z"},"s":"I",  "c":"CONTROL",  "id":7484500>
 5월 28 06:12:56 Arch systemd[1]: mongodb.service: Main process exited, code=exited, status=14/n/a
 5월 28 06:12:56 Arch systemd[1]: mongodb.service: Failed with result 'exit-code'.
```

## 에러 원인

.sock 파일의 사용자 권한으로 인해 발생하는 문제. 소유자를 mongodb 사용자로 변경하면 됨

## 에러 해결

- 임시 해결책

  ```zsh
  sudo rm -rf /tmp/mongodb-27017.sock
  sudo systemctl enable mongodb
  ```

- 해결책

  ```zsh
  sudo chown -R mongodb:mongodb /var/lib/mongodb
  sudo chown mongodb:mongodb /tmp/mongodb-27017.sock
  ```

이후 정상작동 확인

```zsh
$ sudo systemctl status mongodb
● mongodb.service - MongoDB Database Server
     Loaded: loaded (/usr/lib/systemd/system/mongodb.service; enabled; preset: disabled)
     Active: active (running) since Tue 2024-05-28 06:14:07 KST; 3s ago
       Docs: https://docs.mongodb.org/manual
   Main PID: 25130 (mongod)
     Memory: 171.5M (peak: 263.5M)
        CPU: 705ms
     CGroup: /system.slice/mongodb.service
             └─25130 /usr/bin/mongod --config /etc/mongodb.conf

```
