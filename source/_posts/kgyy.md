title: 酷狗/酷狗大字版抓包教程
author: lvlvu
tags:
  - 教程
categories:
  - 羊毛
date: 2022-04-02 14:27:00
---
>请先看[腾讯自选股抓包教程](https://www.yunlife.xyz/txzxg) 

**本教程来自群内管理员**

<img src="/images/pasted-51.png" width=255 height=256 />

<!--more-->

# 前言

有难度，和 [腾讯自选股](https://www.yunlife.xyz/txzxg) 一样需要用到虚拟机。如果自选股已经学会，那难度可以忽略。抓包如果遇到问题可以@qq群里管理员。看到会解答 。

<div class="success">


> 工具


</div>
工具:</br>1.Httpcanary（小黄鸟） </br>  2.RE文件管理器 </br>  3.VMOS pro（虚拟机）


# 教程开始

<div class="info">

> 第一步安装vmos 具体步骤参考自选股教程**（注意：虚拟机安卓版本推荐选择7.1.2.否则可能出现安装软件是提示盗版）**

</div>

<div class="gray">

> 第二步：安装小黄鸟 具体步骤参考自选股教程**（注意：证书安装时如果是安卓12的版本可能出现安装不了。办法如下图）**

</div>


![upload successful](/images/pasted-52.png)


![upload successful](/images/pasted-53.png)


![upload successful](/images/pasted-54.png)


导出文件过后，手机设置里面搜索ca，进去点击刚刚到处的文件，自己安装就行了。过后就不用管小黄鸟里面的提示了。

>第三步：配置证书 参考[腾讯自选股抓包教程](https://www.yunlife.xyz/txzxg)

在虚拟机中获得root权限，导出格式为（xx.0)的格式文件，导入虚拟机，路径为 /sdcard/VMOSfiletransferstation
将其移动到 /etc/security/cacert/ 和 /etc/security/cacerts/ 内，如果只有 /etc/security/cacert/ 那就只放在这里面就行了。

<div class="warning">

> 第四步：抓包 

</div>

1.	在手机用浏览器下载酷狗安装包，然后在VMOS虚拟机里面导入安装包。如果提示是盗版软件，请看第一步
2.	把小黄鸟目标应用设为VMOS PRO	 然后开始抓包
3.	打开虚拟机里面的酷狗 进入·任务中心


![upload successful](/images/pasted-55.png)

然后在小黄鸟的里面找到  *geteway.kugou.com * 开头的一项，点开里面请求一栏



![upload successful](/images/pasted-56.png)

复制红圈里的全部内容，如果无法复制就点击最底下的Raw栏进去复制。收工！










