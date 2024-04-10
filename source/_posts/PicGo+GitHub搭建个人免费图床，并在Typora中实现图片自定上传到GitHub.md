---
title: PicGo+GitHub搭建个人免费图床，并在Typora中实现图片自定上传到GitHub
date: 2024/4/10 上午9:42
categories: 
- 记录
tags: 
- PicGo
- github
- 图床
- Typora
---
2024/4/10 上午9:23

### PicGo+GitHub搭建个人免费图床，并在Typora中实现图片自定上传到GitHub

本文介绍使用`PicGo`+`GitHub`搭建免费图床，主要实现在`Typora`中写个人博客是图片可自动上传。

1. 新建`GitHub`仓库并进行配置

   ​	

   **注意需要设置为公共仓库**

   ![新建GitHub仓库](https://cdn.jsdelivr.net/gh/hkp4570/ImagePicGo@main/img/%E6%96%B0%E5%BB%BAGitHub%E4%BB%93%E5%BA%93.png)
<!--more-->
2. 进入设置页面，打开`**Developer settings**`，创建新的`token`，并进行设置。

   ![个人设置](https://cdn.jsdelivr.net/gh/hkp4570/ImagePicGo@main/img/%E4%B8%AA%E4%BA%BA%E8%AE%BE%E7%BD%AE.png)

   ![开发者设置](https://cdn.jsdelivr.net/gh/hkp4570/ImagePicGo@main/img/%E5%BC%80%E5%8F%91%E8%80%85%E8%AE%BE%E7%BD%AE.png)

   ![新建token](https://cdn.jsdelivr.net/gh/hkp4570/ImagePicGo@main/img/%E6%96%B0%E5%BB%BAtoken.png)

![token设置](https://cdn.jsdelivr.net/gh/hkp4570/ImagePicGo@main/img/token%E8%AE%BE%E7%BD%AE.png)

​	   **过期时间可设置为不过期，Select scopes只勾选repo就可以**

3. 配置`PicGo`

   首先到[官网](https://github.com/Molunerfinn/PicGo/releases)进行下载，下载慢的话可以使用国内镜像源，[官网首页](https://github.com/Molunerfinn/PicGo)有对应的地址。最好使用稳定的版本。目前稳定版本是v2.3.1。

   下载完成后安装并运行，在Mac中运行时可能会报错文件已经损坏，请参考此[博客](https://blog.csdn.net/m0_49562857/article/details/128998691)解决。

   运行后配置GitHub

   ![PicGo设置](https://cdn.jsdelivr.net/gh/hkp4570/ImagePicGo@main/img/PicGo%E8%AE%BE%E7%BD%AE.png)

> ​	自定义域名配置了好几次才成功，可能粘贴的时候不是纯文本的原因。最好不要使用默认域名，速度贼慢

​		配置完成后打开上传区，上传文件，如果相册中有你上传的文件说明已经配置生效了。如果失败的话可以		日志文件查看报错信息。

4. 配置`Typora`

   在使用Typora时，当我们粘贴图片时，想要让图片自动上传图床。这是需要打开设置，点击图像选项，配置上传服务。

   ![Typora图像设置](https://cdn.jsdelivr.net/gh/hkp4570/ImagePicGo@main/img/Typora%E5%9B%BE%E5%83%8F%E8%AE%BE%E7%BD%AE.png)

   ![Typora图像验证](https://cdn.jsdelivr.net/gh/hkp4570/ImagePicGo@main/img/Typora%E5%9B%BE%E5%83%8F%E9%AA%8C%E8%AF%81.png)

> 不能上传重复的图片，否则会上传不成功。

