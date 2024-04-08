---
title: hexo+GitHub搭建静态页面常见问题
date: 2024-04-08 11:15:40
categories: 
- 记录
tags: 
- hexo
- github
---

#### 部署代码时需要输入用户名和密码

![截屏2024-04-08 11.15.40](1.png)

<!--more-->

是因为deploy配置的repo是https的地址

![截屏2024-04-08 11.17.02](2.png)

把配置改为ssh

![截屏2024-04-08 11.21.27](3.png)

#### 执行hexo g 命令之后html文件为空，而且控制台有No Layout

![截屏2024-04-08 11.32.21](4.png)

这种情况可能是`_config.yml`配置文件中theme的配置的是一个没有下载过的主题，这时候可以到[主题网站](https://hexo.io/themes/)下载对应的主题。重新执行就可以了。