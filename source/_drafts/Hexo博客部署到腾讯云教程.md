---
title: Hexo博客部署到腾讯云服务器教程
author: 墨白
img: /medias/featureimages/6.jpg
coverImg: /medias/featureimages/6.jpg
top: false
cover: false
toc: true
mathjax: false
tags:
  - hexo
  - 腾讯云
  - 部署
  - null
  - null
categories:
  - 随笔
  - 原创
abbrlink: 1685409089
date: 2020-01-02 09:39:25
password:
summary:
---

> 本篇内容用来讲述如何将 hexo 博客部署到腾讯云的服务器上。
>
> 1. 云服务器端 git 的配置
> 2. Nginx 的配置
> 3. 本地端 hexo 的设置更改

# 前言

最近趁着腾讯云在做活动，买了1年的服务器。正好自己的博客之前是搭建在 coding 上的，现在也可以顺便部署到腾讯云上了。其实过程蛮简单的，即使，你是个对后台一窍不通的小白，也能很容易部署成功。

* **前期需要准备：**

1. 一个腾讯云服务器
2. 本地链接远程服务器工具[Xshell6客户端]( https://xshell.en.softonic.com/ )
3. hexo 本地博客

顺便说下我的服务器环境：

| 操作系统 | CPU  | 内存 | 带宽  |
| -------- | ---- | ---- | ----- |
| Cenos7.6 | 1核  | 2GB  | 1Mbps |

## 进入云服务器中

1. 首先点击下边网站，登录你的进入云服务器的控制台
   腾讯云服务器的控制台：[传送门](https://console.cloud.tencent.com/cvm/index)
2. 左边菜单选择云主机，然后找到你的服务器。点击登录

![](F:%5Cmobai_images.gitee.io%5Cimg%5Chexocoding%5C3.png)

1. 获取动态验证码

![](F:%5Cmobai_images.gitee.io%5Cimg%5Chexocoding%5C4.jpg)

2. 通过xshell远程链接你的云服务器

![](F:%5Cmobai_images.gitee.io%5Cimg%5Chexocoding%5C5.jpg)

3. 输入你的云服务器公网IP地址,输入密码，进入 云服务器 CentOS中。（初始密码在控制台右上角的消息列表中）

![image-20200102100043422](F:%5Cmobai_images.gitee.io%5Cimg%5Chexocoding%5C6.jpg)

4. 链接成功以后出现如下界面

   ![](F:%5Cmobai_images.gitee.io%5Cimg%5Chexocoding%5C7.jpg)

## 云服务器端配置 git

* 安装依赖库：

~~~nginx
yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel 
~~~

*  安装编译工具： 

~~~nginx
yum install gcc perl-ExtUtils-MakeMaker package
~~~

* 下载git

1. 选择一个目录来存放下载下来的 git 安装包。这里选择了`/usr/local/` 目录

~~~nginx
cd /usr/local/
~~~

2. 到官网找一个新版稳定的源码包下载到 `/usr/local/` 文件夹里,我这里下载的是最新版本的

```bash
wget https://www.kernel.org/pub/software/scm/git/git-2.9.5.tar.gz
```

![](F:%5Cmobai_images.gitee.io%5Cimg%5Chexocoding%5C8.jpg)

### 解压编译 git

1. 在当前目录下解压 `git-2.9.5.tar.gz`

~~~bash
tar -zvxf git-2.9.5.tar.gz
~~~

2. 进入到git目录下

~~~bash
cd git-2.9.5
~~~

3. 执行编译

~~~bash
make all prefix=/usr/local/git-2.9.5
~~~

![image-20200102103107288](F:%5Cmobai_images.gitee.io%5Cimg%5Chexocoding%5C9.jpg)

1. 安装 git 到 `/usr/local/git` 目录下

```bash
make install prefix=/usr/local/git
```

### 配置 git 环境变量

1. 将 git 加入 PATH 目录中

```bash
echo 'export PATH=$PATH:/usr/local/git/bin' >> /etc/bashrc
```

2. 使 git 环境变量生效

```bash
source /etc/bashrc
```

3. 查看版本

```bash
git --version
```

显示入下图,说明你已经安装成功了

![image-20200102103509623](F:%5Cmobai_images.gitee.io%5Cimg%5Chexocoding%5C10.jpg)

### 创建Git仓库

* 创建 git 仓库，用于存放博客网站资源。

* 在 `home/git` 的目录下，创建一个名为`hexoBlog`的裸仓库（bare repo）。
* 如果没有 `home/git` 目录，需要先创建；然后修改目录的所有权和用户权限。

```bash
mkdir /home/git/
chown -R $USER:$USER /home/git/
chmod -R 755 /home/git/
```

![image-20200102103715163](F:%5Cmobai_images.gitee.io%5Cimg%5Chexocoding%5C11.jpg)

 然后，执行如下命令： 

```bash
cd /home/git/
git init --bare hexoBlog.git
```

刚才这一步主要创建一个裸的 git 仓库。

1. 创建一个新的 git 钩子，用于自动部署。 

   1. 在 `/home/git/hexoBlog.git` 下，有一个自动生成的 `hooks` 文件夹。我们需要在里边新建一个新的钩子文件 `post-receive`。

   ![image-20200102103948169](F:%5Cmobai_images.gitee.io%5Cimg%5Chexocoding%5C12.jpg)

   ~~~bash
   vim /home/git/hexoBlog.git/hooks/post-receive
   ~~~

1. 按 `i` 键进入文件的编辑模式，在该文件中添加两行代码（将下边的代码粘贴进去)，指定 Git 的工作树（源代码）和 Git 目录（配置文件等）。

   ```bash
   #!/bin/bash
   git --work-tree=/home/hexoBlog --git-dir=/home/git/hexoBlog.git checkout -f
   ```

然后，按 `Esc``:wq`

1. 修改文件权限，使得其可执行。

```bash
chmod +x /home/git/hexoBlog.git/hooks/post-receive
```

### nginx配置

