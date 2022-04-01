title: PVE 安装及使用经验（持续更新）
tags: 学习笔记
categories: [学习笔记]
date: 2022-04-01 15:37:42
---
>接触Linux之后，发现虚拟机的可玩性确实很高，对我而言，虚拟系统目前可选的有 ESXI 与 PVE ，二者仁者见仁智者见智吧！而我选择了PVE（Proxmox） ，目前在PVE上已经装了openwrt、win7、win10、centos……</br>这篇文章用来记录我的整个安装到使用的经验吧!

<img src="/images/pasted-34.png" width=350 height=256 />

<!--more-->
# PVE的安装
<div class="success">

> PVE安装教程确实太多了，这里就引用一篇我使用的教程吧!       原文链接：https://www.10bests.com/install-proxmox-ve/
</div>

## 下载PVE ISO文件

官方网站下载地址：https://www.proxmox.com/en/downloads ，选择BT下载会快很多。

## PVE安装U盘制作

插入U盘，使用UltralISO打开下载的ISO镜像，点击启动 > 写入硬盘映像... > 选择U盘 > 选择写入方式为“RAW” > 写入。

## 安装PVE
>1.插入PVE安装U盘，打开电脑从PVE安装U盘引导启动，选择“Install Proxmox VE”，按回车开始安装。


![upload successful](/images/pasted-35.png)


>2.单击“I agree”同意协议，进入下一步。



![upload successful](/images/pasted-36.png)


>3.选择要安装的硬盘，单击“Options”可以选择硬盘格式或者安装到zfs RAID硬盘阵列，要提前准备好多块硬盘，完成后单击“Next”进入下一步。.

PVE可以选择安装到U盘上，PVE安装完后也会利用U盘自动生成存储空间，不像EXSi需要自己创建。我主力机上用的是闪迪CZ430酷豆，体积小巧速度也很快，PVE管理界面都很流畅。一般ITX主板上只有一个m.2接口，可以留着直通给Win10等系统用，SATA控制器直通给虚拟群晖。


![upload successful](/images/pasted-37.png)


>4.输入国家选择时区，这里国家不能选择，需要键盘输入“China”。


![upload successful](/images/pasted-38.png)

>5.输入root密码和电子邮件地址，单击“Next”。


![upload successful](/images/pasted-39.png)

>6.选择管理接口，输入PVE节点的服务器名、IP地址、子网掩码、网关和DNNS服务器，如果电脑连到网络，后面的这些信息会自动获取，也可以自己改。

<div class="warning">

> 注意：PVE只有通过管理接口连接的网卡才能登录到PVE的管理界面，这跟EXSi不一样，EXSi配置好默认任何一个网卡都能访问管理界面。

</div>

![upload successful](/images/pasted-40.png)


>7.确认安装信息，点击“Install”开始安装，如果有不对的就点“Previous”回去修改。


<div class="warning">

> **注意**：安装过程会格式安装的磁盘，请确保安装的磁盘上没有重要数据。

</div>


![upload successful](/images/pasted-41.png)


>8.PVE很轻量，装过程很快，就算安装到闪迪CZ430酷豆U盘上也就一分钟多点。



![upload successful](/images/pasted-49.png)

>9.安装完成，单击“Reboot”，记得拔掉PVE安装U盘并更改启动项。


![upload successful](/images/pasted-44.png)

>10.PVE的启动选项，第一个就算PVE系统，默认等待5S，从硬盘启动PVE。

![upload successful](/images/pasted-45.png)

>11.启动完成，下面红框就算PVE的管理地址。

![upload successful](/images/pasted-46.png)
>12.用浏览器访问PVE的管理地址，这里Url要做到“一字不差”地输入到浏览器，输入root用户名和密码，单击“登录”。

语言有中文可选，PVE汉化支持很好。



![upload successful](/images/pasted-47.png)

>13.进入PVE的管理界面。大功告成！


![upload successful](/images/pasted-48.png)







