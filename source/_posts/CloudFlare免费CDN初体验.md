---
title: CloudFlare + 腾讯云免费CDN初体验
author: 墨白
top: false
cover: false
toc: true
mathjax: false
tags:
  - CDN
  - null
  - null
  - null
categories:
  - Hexo
abbrlink: 3313221001
date: 2020-03-20 11:15:52
img:
coverImg:
password:
summary:
---



> 最近总是有人说我的博客访问很慢,但是我自己测试的时候就是很快啊,缓存也清理了,重新加载也不慢,这个问题弄得有点尴尬了,那就听你们的,弄个CDN加速一下吧,今天选的是[CloudFlare](https://dash.cloudflare.com)这款免费的CDN.

![]( https://wang_lianjie.gitee.io/mobai_blog.gitee.io/img/20203.20/1.jpg )

### CloudFlare的使用超级简单

* #### 首先，我们注册一个账号

![注册账号](https://wang_lianjie.gitee.io/mobai_blog.gitee.io/img/20203.20/2.jpg)

* #### 登录进去进到主页,点击添加站点

![添加站点]( https://wang_lianjie.gitee.io/mobai_blog.gitee.io/img/20203.20/3.jpg )

![添加你自己的域名]( https://wang_lianjie.gitee.io/mobai_blog.gitee.io/img/20203.20/4.jpg )

* #### 选择第一个面向个人博客

![选择第一个]( https://wang_lianjie.gitee.io/mobai_blog.gitee.io/img/20203.20/5.jpg )

* #### 这个时候CloudFlare会扫描我们站点的配置

![扫描站点配置]( https://wang_lianjie.gitee.io/mobai_blog.gitee.io/img/20203.20/6.jpg )

* #### 需要修改域名DNS服务器地址

![修改DNS]( https://wang_lianjie.gitee.io/mobai_blog.gitee.io/img/20203.20/7.jpg )

#### 比如我是腾讯云的域名,那么我就要在腾讯云修改我域名的DNS服务器,步骤如下

* #### 登录腾讯云,进入控制台,选择域名管理,点击你选择加速的域名,选择更多DNS修改

![]( https://wang_lianjie.gitee.io/mobai_blog.gitee.io/img/20203.20/7.1.jpg )

* #### 把CloudFlare提供的服务器地址粘贴过来确认提交即可

![](https://wang_lianjie.gitee.io/mobai_blog.gitee.io/img/20203.20/7.2.jpg )

* #### 最后,我们可以配置一些关于安全和速度相关的设置,至此,就搞定了

![](https://wang_lianjie.gitee.io/mobai_blog.gitee.io/img/20203.20/8.jpg )