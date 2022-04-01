title: Linux使用笔记
author: lvlvu
tags:
  - 学习笔记
categories: [学习笔记]
date: 2022-03-26 11:33:00
---
>以下为本人Linux学习过程中所常用到的命令以及问题解决方案，乱序！

<div class="yellow">
  
>更新日期：2022/3/26
  
  </div>

# 清除端口占用
在本例中，假设8080端口被占用。

1.查看8080端口是否被占用

```netstat -anp | grep 8080``` 

输出结果：

```tcp 0 0 :::8080 :::* LISTEN 3000/java```

由上可知8080端口已经被开启。

2.查看占用8080端口的进程：

```fuser -v -n tcp 8080```

输出结果：

```USER        PID   ACCESS COMMAND   8080/tcp:```

```zhu        1154    F.... java```

3.杀死占用8080端口的进程：

```kill -s 9 1154```(自己的进程号).

4.查看所有进程：

```ps```

输出结果：

```PID TTY          TIME CMD```

```2949 pts/1    00:00:00 bash```

```3037 pts/1    00:00:00 ps```

这是便可发现1154进程已经不存在了。
# Linux网络设置（IP/网关/DNS）
## 修改IP地址

ifconfig eth0 192.168.1.80

这样就把IP地址修改为192.168.1.80(如果发现上不了网了，那么你可能需要把网关和DNS也改一下，后面会提到)，但是当你重新启动系统或网卡之后，还是会变回原来的地址，这种修改方式只适用于需要临时做IP修改。要想永久性修改，就要修改/etc/sysconfig/network-scripts/ifcfg-eth0这个文件，这个文件的主要内容如下（你的文件中没有的项，你可以手动添加）：

```vi  /etc/sysconfig/network-scripts/ifcfg-eth0```

DEVICE=eth0 #描述网卡对应的设备别名
BOOTPROTO=static #设置网卡获得ip地址的方式，选项可以为为static，dhcp或bootp
BROADCAST=192.168.44.255 #对应的子网广播地址
HWADDR="00:0C:29:6B:2E:7B"#对应的网卡物理地址
IPADDR=192.168.44.137 #只有网卡设置成static时，才需要此字段
NETMASK=255.255.255.0 #网卡对应的网络掩码
NETWORK=192.168.44.0 #网卡对应的网络地址，也就是所属的网段
ONBOOT=yes #系统启动时是否设置此网络接口，设置为yes时，系统启动时激活此设备

 

 

## 修改网关

```route add default gw 192.168.1.1 dev eth0```

这样就把网关修改为192.168.1.1了，这种修改只是临时的，当你重新启动系统或网卡之后，还是会变回原来的网关。要想永久性修改，就要修改/etc/sysconfig/network 这个文件，这个文件的主要内容如下（你的文件中没有的项，你可以手动添加）：

```vi  /etc/sysconfig/network```

NETWORKING=yes #表示系统是否使用网络，一般设置为yes。如果设为no，则不能使用网络。

HOSTNAME=centos #设置本机的主机名，这里设置的主机名要和/etc/hosts中设置的主机名对应

GATEWAY=192.168.1.1 #设置本机连接的网关的IP地址。

**********上面的文件修改完要重新启动一下网卡才会生效：
```service network restart ```********

## 修改DNS

上面的都修改完之后，当你ping一个域名是肯能不通，但ping对应的IP地址是同的，这时我们需要修改一下DNS。修改DNS要通过修改/etc/resolv.conf这个文件：

```vi /etc/resolv.conf```

nameserver 8.8.8.8 #google域名服务器 nameserver 8.8.4.4 #google域名服务器

通过上面的所有设置，系统应该可以上网了。

<div class="warning">

> 如果centos系统建立在虚拟机之上，那么在设置虚拟机的网络时请选择‘网桥适配器’连接。**

</div>