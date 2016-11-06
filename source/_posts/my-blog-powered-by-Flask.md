layout: post
title: My Blog
date: 2016-11-06 16:37:55
tags:
---
### Targets:
* have my own blog website,which supports with comments and Google Analytics
* interface similar to HEXO
<!-- more -->

# 1.server setting

* 1.change root password
``` bash
$ passwd
```

* 2.add account
``` bash
$ adduser will
$ passwd will
$ visudo
add will	ALL=(ALL)	ALL
```

* 3.disable root login by ssh
``` bash
$ vi /etc/ssh/sshd_config 
$ systemctl restart sshd.service
```

* 4.setup firewalld
``` bash
$ yum install firewalld
$ systemctl start firewalld
```

* 5.use ssh key to login
``` bash
$ ssh-keygen -t rsa 
$ cat .ssh/id_rsa.pub >> .ssh/authorized_keys
$ cat id_rsa.pub >> .ssh/authorized_keys
$ chmod 700 .ssh/
$ chmod 600 .ssh/authorized_keys
```

* 5.disable password login
``` bash
$ vi /etc/ssh/sshd_config 
```