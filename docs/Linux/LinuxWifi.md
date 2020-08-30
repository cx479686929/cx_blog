---
id: LinuxWifi
title: Linux环境下开启wifi热点
author: 一代风流～
author_title: To be the weirdest person
author_url: https://blog.csdn.net/qq_43176366
author_image_url: /img/cx-head.jpg
---

起因

　　由于校园网对设备的限制，每个账号只能让两个设备登录，但是我有一台电脑，一个树莓派，两部手机，一个ipad，老是切来切去很麻烦(虽然没同时用)。

　　所以我想到的办法是用一台设备连接wifi后分享出去，即wifi热点。

　　在Windows下是可以直接用的，但是在linux环境下貌似不能，我的系统是Deepin 15.11 有一个热点，但是连接后会断开ＷｉＦｉ连接，貌似这个的场景是连接网线后开热点。
<!--truncate-->

# 方法

采用的是github上的create_ap项目

如果安装了git,克隆安装create_ap

```bash
git clone https://github.com/oblique/create_ap 
 
cd create_ap 
 
sudo make install
```

如果提示没有安装git

```bash
sudo apt-get install git
```

### 如何使用：

此程序依赖hostapd,iptables,dnsmasq，如果没有安装，请先安装

```bash
sudo apt-get install hostapd iptables dnsmasq
```

如果你的无线网卡名是wlan0,有线网卡名是eth0,你想创建的热点是myhost,密码是12345678

```bash
sudo create_ap wlan0 eth0 myhost 12345678 #开启热点但是依赖终端，和下条命令二选其一
sudo nohup create_ap wlan0 eth0 myhost 12345678 &  #开启热点并后台运行，可以关闭终端

```

如何查看网卡名

```bash
ifconfig #冒号前的就是你的网卡名
cat /proc/net/dev | awk '{if($2>0 && NR > 2) print substr($1, 0, index($1, ":") - 1)}' #这条命令会列出你的所有网卡名
```

### 之后就可以都所有设备都上网了。

### 如何卸载
```bash
make uninstall
```

