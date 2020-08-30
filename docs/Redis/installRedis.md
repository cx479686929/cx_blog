---
id: installRedis
title: Redis安装
author: 一代风流～
author_title: To be the weirdest person
author_url: https://blog.csdn.net/qq_43176366
author_image_url: /img/cx-head.jpg

---

## 可以先看到本文末尾

# 安装：

1.获取redis资源

```bash
wget http://download.redis.io/releases/redis-4.0.8.tar.gz
```
<!--truncate-->

2.解压

```bash
tar xzvf redis-4.0.8.tar.gz
```
3.安装
```bash
cd redis-4.0.8
make
cd src
make install PREFIX=/usr/local/redis

```
如果make不行就要先安装下 
```bash
sudo apt-get install build-essential
```
4.移动配置文件到安装目录下

```bash
cd …/

mkdir /usr/local/redis/etc

mv redis.conf /usr/local/redis/etc
```

5.配置redis为后台启动

```bash
vi /usr/local/redis/etc/redis.conf #将daemonize no 改成daemonize yes


```

6.将redis加入到开机启动

```bash
vi /etc/rc.local #在里面添加内容：/usr/local/redis/bin/redis-server /usr/local/redis/etc/redis.conf (意思就是开机调用这段开启redis的命令)


```

7.开启redis

```bash
/usr/local/redis/bin/redis-server /usr/local/redis/etc/redis.conf
```

8.将redis-cli,redis-server拷贝到bin下，让redis-cli指令可以在任意目录下直接使用

```bash
cp /usr/local/redis/bin/redis-server /usr/local/bin/

cp /usr/local/redis/bin/redis-cli /usr/local/bin/
```

9.设置redis密码

a.运行命令：redis-cli

b.查看现有的redis密码(可选操作，可以没有)

运行命令：config get requirepass 如果没有设置过密码的话运行结果会如下图所示

c.设置redis密码

运行命令：config set requirepass ****(****为你要设置的密码)，设置成功的话会返回‘OK’字样

d.测试连接

重启redis服务

//（redis-cli -h 127.0.0.1 -p 6379 -a ****（****为你设置的密码））

输入 redis-cli 进入命令模式，使用 auth ‘*****’ （****为你设置的密码）登陆

10.让外网能够访问redis

a.配置防火墙: firewall-cmd --zone=public --add-port=6379/tcp --permanent（开放6379端口）

systemctl restart firewalld（重启防火墙以使配置即时生效）

查看系统所有开放的端口：firewall-cmd --zone=public --list-ports

b.此时 虽然防火墙开放了6379端口，但是外网还是无法访问的，因为redis监听的是127.0.0.1：6379，并不监听外网的请求。

（一）把文件夹目录里的redis.conf配置文件里的bind 127.0.0.1前面加#注释掉

（二）命令：redis-cli连接到redis后，通过 config get daemonize和config get protected-mode 是不是都为no，如果不是，就用config set 配置名 属性 改为no。

## 其实也可以简单安装

```bash
sudo apt-get install redis-server
```


1
启动

```bash
redis-server

```

1
运行客户端

```bash
redis-cli
```

