---
layout: post
title: rsp_02_setup.md
date: 2018-09-16 22:18:36
tags:
- Raspberry
---
In this article, I'll show you follow:

- write raspberry to sd card
- set up wifi password headlessly(without cable or monitor)
- enable ssh as default
- set static ip

<!-- more -->

### write .img to sd card

```bash
# in dd command, /dev/sdc is your sd card
cd ~/Downloads
wget -c http://director.downloads.raspberrypi.org/raspbian_lite/images/raspbian_lite-2018-06-29/2018-06-27-raspbian-stretch-lite.zip
dd bs=4M if=~/Downloads/2018-04-18-raspbian-stretch.img of=/dev/sdc conv=fsync
```

### set up wifi

create a file named wpa_supplicant.conf in boot partition(/media/username/boot/wpa_supplicant.conf), which has content like this:

```none
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=GB

network={
        ssid="Your wifi"
        psk="Your password"
}
```

### set static ip

edit /media/username/rootfs/etc/dhcpcd.conf, add lines like follow:

```none
interface eth0
static ip_address=192.169.1.64/24
static routers=192.168.1.1
static domain_name_servers=114.114.114.114

interface wlan0
static ip_address=192.168.1.65/24
static routers=192.168.1.1
static domain_name_servers=114.114.114.114
```

### enable ssh

```bash
touch /media/username/boot/ssh
```

Above all.