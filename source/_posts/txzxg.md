title: 腾讯自选股抓包教程
sticky: 100
tags:
  - 教程
categories:
  - 羊毛
date: 2022-03-29 11:19:00
---
# 前言
> **事先说，这个教程难度和复杂程度远超快手极速版抓包，请做好心理准备！**


<!-- more -->

<div class="success">

> 说在前面

</div>
考虑到多数人没有抓包经验，甚至没听说过“root”一词，本教程基于一台普通未root安卓手机进行教程。
<div class="info">

> 抓包工具

</div>
1.Httpcanary（抓包工具，以下简称小黄鸟）</br>2.RE文件管理器</br>3.VMOS（虚拟机）
<div class="yellow">

> 原理说明
</div>

利用小黄鸟抓包需要安装CA证书，安装证书需要ROOT权限移动证书位置，手机未ROOT情况下，利用VMOS虚拟机，虚拟一个具有ROOT权限的安卓手机，在虚拟的安卓手机中安装腾讯自选股，然后抓包，over！
<div class="success">

> 教程开始

</div>

# 安装VMOS

请进入[VMOS官网](http://www.vmos.cn/)，或通过手机应用商店下载即可！
**注：VMOS创建具有root权限的手机为VIP功能，好像是一个月十几块，支持正版！当然你也可以另找“免费版”，或联系我！**

安装之后，创建一个虚拟机，我选择的是具有root权限的安卓7.1版本，然后开机。

![upload successful](/images/pasted-11.png)

在虚拟机系统中安装RE文件管理器，完成第一步。

# 安装小黄鸟

*本文演示的小黄鸟版本号为HttpCanary_v3.3.6* </br>ps:QQ群内有两个版本，选择任意一个你可以用的版本即可，界面大同小异，功能一样！
<div class="warning">

> 安装后进入小黄鸟，依次配置VPN→安装证书→移动证书到CA列表，由于手机未root，移动证书这一步会报错，直接**跳过**就好。

PS：高版本的小黄鸟貌似没有着一步，忽略就好。

</div>

<div class="yellow">

> 各个手机安装证书的方式不一样，有的会提示 **请进入设置安装CA证书** 此时就需要你根据你的机型去[百度](www.baidu.com) 证书方式。</br>

主要方式大同效益：导出证书→进入设置搜索CA证书安装→找到刚才导出的CA证书点击安装即可

证书格式有两个，选择 **xxx.pem**

</div>

<div class="waring">

> 如果你开始抓包，提示没有网络，则证明CA证书没有安装成功!

</div>

![upload successful](/images/pasted-12.png)


![upload successful](/images/pasted-13.png)


![upload successful](/images/pasted-14.png)


<div class="success">

> 配置证书

</div>

依次点击设置→HttpCanary根证书→导出证书→（.0）格式→**记住文件名与文件位置**


![upload successful](/images/pasted-15.png)



![upload successful](/images/pasted-16.png)


![upload successful](/images/pasted-17.png)


![upload successful](/images/pasted-18.png)

进入VMOS虚拟机，将刚才所导出的证书导入到虚拟机内部。

![upload successful](/images/pasted-19.png)

![upload successful](/images/pasted-20.png)

![upload successful](/images/pasted-21.png)


![upload successful](/images/pasted-22.png)


![upload successful](/images/pasted-23.png)
打开刚才安装的RE文件管理器，找到刚才所导入的问价，路径为 **/sdcard/VMOSfiletransferstation**
将其移动到 **/etc/security/cacert/** 和 **/etc/security/cacerts/** 内</br>
如果只有 **/etc/security/cacert/** 那就只放在这里面就行了</br>
OK，配置证书完成!

# 开始抓包
## 公众号抓包
 
将小黄鸟目标应用设定为**微信** ，然后开起抓包
![upload successful](/images/pasted-24.png)

![upload successful](/images/pasted-25.png)

关注微信公众号*腾讯自选股微信版|微证券* →右下角 *好福利* → *福利中心*


![upload successful](/images/pasted-26.png)

回到小黄鸟，找到为 **wzq.tenpay.com** 链接的包，点进去！

![upload successful](/images/pasted-27.png)

![upload successful](/images/pasted-28.png)

<div class="success">

> 点击**请求**，记录  wzq_qlskey=zz&wzq_qluin=aa  ，搞定第一步

</div>

## 抓APP包

进入 VMOS 下载 **腾讯自选股app** 并登陆


<div class="warning">

> 将小黄鸟目标应用设定为**VMOS** ，然后开起抓包

</div>

回到VMOS，进入 **腾讯自选股**，点击左上角头像，进入 *福利中心*

![upload successful](/images/pasted-29.png)

 
![upload successful](/images/pasted-30.png)



![upload successful](/images/pasted-31.png)

<div class="info">

> 然后回到小黄鸟界面找到 **wzq.tenpay.com** 链接的包，点进去！

</div>

![upload successful](/images/pasted-32.png)


![upload successful](/images/pasted-33.png)


<div class="success">

> 点击**请求**，记录 openid=xx&fskey=yy ，搞定！

</div>

<div class="warning">

> 最后一起整理为  </br>
`openid=xx&fskey=yy&wzq_qlskey=zz&wzq_qluin=aa`

</div>
<div class="warning">

> 转载请注明出处，谢谢！

</div>