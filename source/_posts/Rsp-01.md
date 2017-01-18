layout: post
title: Rsp_01_vnc
date: 2017-01-16 19:33:47
tags: Raspberry
---
树莓派的常用功能配置：
* Vnc viewer
* Vsftpd

<!-- more -->
### 1. Vnc viewer
``` bash
$ sudo apt-get install tightvncviewer
$ tightvncserver
$ vncserver :1 -geometry 800x600 -depth 24
```

### 2. Vsftpd
``` bash
$ sudo apt-get install vsftpd
$ sudo service vsftpd start
```
