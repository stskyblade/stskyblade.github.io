layout: post
title: My Blog
date: 2016-11-06 16:37:55
tags: 服务器配置
---
### Targets:
* have my own blog website,which supports with comments and Google Analytics
* interface similar to HEXO
<!-- more -->

### 1.Server setting

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

* 6.disable password login
``` bash
$ vi /etc/ssh/sshd_config
```

### 2.LNMP setting

* 1.install Nginx
``` bash
$ yum install Nginx
$ systemctl start nginx
$ systemctl enable nginx
```

* 2.install MariaDB
``` bash
$ yum install mariadb-server
$ systemctl start mariadb
$ systemctl enable mariadb
$ /usr/bin/mysql_secure_installation
```

* 3.install PHP5
``` bash
$ yum install php-fpm php-mysql
$ systemctl start php-fpm
$ systemctl enable php-fpm
$ mkdir /var/lib/php/session/
$ chown -R apache:apache /var/lib/php/session/
$ nano /etc/nginx/nginx.conf
# location ~ \.php$ {
#
# 　　root           path;   
# 　　fastcgi_pass　　127.0.0.1:9000;           
# 　　fastcgi_index　  index.php;            
# 　　fastcgi_param　SCRIPT_FILENAME  $document_root/$fastcgi_script_name;            
# 　　include       　　  fastcgi_params;        
#
# }
$ systemctl reload nginx
```

* 4.install vsftpd
``` bash
$ yum install vsftpd
$ systemctl start vsftpd.service
$ systemctl enable vsftpd.service
$ usermod -a -G nginx username
$ chown -R :nginx path
$ chmod -R g+rw path
```

* 5.install phpmyadmin
``` bash
continue
```
