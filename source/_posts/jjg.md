title: 羊毛合集
author: lvlvu
tags:
  - 羊毛
categories:
  - 羊毛
date: 2022-03-27 10:11:00
---

# 青龙面板的安装
## docker run
```
docker run -dit \
-v $pwd/root/ql/config:/ql/config \
-v $pwd/root/ql/log:/ql/log \
-v $pwd/root/ql/db:/ql/db \
-v $pwd/root/ql/scripts:/ql/scripts \
-v $pwd/root/ql/jbot:/ql/jbot \
-v $pwd/root/ql/repo:/ql/repo \
-v $pwd/root/ql/deps:/ql/deps \
-p 5700:5700 \
-e ENABLE_HANGUP=true \
-e ENABLE_WEB_PANEL=true \
--name qinglong \
--hostname qinglong \
--restart always \
whyour/qinglong:2.10.13
```
## 多容器青龙

```
docker run -dit \
 -v $pwd/root/ql2/config:/ql/config \
-v $pwd/root/ql2/log:/ql/log \
 -v $pwd/root/ql2/db:/ql/db \
 -v $pwd/root/ql2/scripts:/ql/scripts \
 -v $pwd/root/ql2/jbot:/ql/jbot \
 -v $pwd/root/ql2/repo:/ql/repo \
 -v $pwd/root/ql2/deps:/ql/deps \
 -p 5702:5700 \
 -e ENABLE_HANGUP=true \
 -e ENABLE_WEB_PANEL=true \
 --name qinglong2 \
 --hostname qinglong2 \
--restart always \
whyour/qinglong:2.10.13
```