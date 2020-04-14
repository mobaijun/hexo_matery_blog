---
title: Hexo常用命令
author: 墨白
img: 
coverImg: 
top: false
cover: false
toc: true
mathjax: false
tags:
  - hexo
  - null
  - null
  - null
categories:
  - Hexo
abbrlink: 617278059
date: 2019-12-30 09:12:22
password:
summary:
---

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=100% height=86 src="//music.163.com/outchain/player?type=2&id=547614214&auto=0&height=66"></iframe>
利用Hexo搭建号博客以后我们需要知道常用的几条命令

### 新建一篇客

~~~bash
$ hexo new [layout] [Article name]
~~~

*  这样会在`source/_post`中新建一个`Article name.md`文件,你就可以在打开这个`.md`文件进行写文章了😁

> `layout` 可选参数，用以指定文章类型，若无指定则默认由博客根目录下的.yml配置文件中的 default_layout 选项决定

> `title` 必填参数，用以指定文章标题，如果参数值中含有空格，则需要使用双引号包围

### 新建一篇草稿

* 如果你不想这篇博客上传到线上,你可以新建一篇草稿

~~~bash
$ hexo new draft "Article name"
~~~

*  这样会在`source/_draft`中新建一个`Article name.md`文件，如果你的草稿文件在写的过程中，想要预览一下，那么可以使用 

~~~bash
$ hexo server --draft
~~~

* 如果你的草稿文件写完了，想要发表到`post`中，

~~~bash
$ hexo publish draft "Article name"
~~~

*  博客就会自动把`Article name.md`,移动到`post`中。 

### 初始化博客

*  初始化本地文件夹为网站的根目录 

~~~bash
$ hexo init [folder]
~~~

* `folder` 可选参数，用以指定初始化目录的路径，若无指定则默认为当前目录

### hexo clean

* `hexo clean` 命令用于清理缓存文件，是一个比较常用的命令

```bash
$ hexo clean
```

### Option

#### （1）hexo --safe

`hexo --safe` 表示安全模式，用于禁用加载插件和脚本

```bash
$ hexo --safe
```

**安装新插件时遇到问题可尝试此操作**

#### （2）hexo --debug

`hexo --debug` 表示调试模式，用于将消息详细记录到终端和 `debug.log` 文件

```bash
$ hexo --debug
```

#### （3）hexo --silent

`hexo --silent` 表示静默模式，用于静默输出到终端

```bash
$ hexo --silent
```

### 生成博客静态文件

hexo generate` 命令用于生成静态文件，一般可以简写为 `hexo g

```bash
$ hexo generate
```

* `-d` 选项，指定生成后部署，与 `hexo d -g` 等价

### 本地服务器预览

hexo server` 命令用于启动本地服务器，一般可以简写为 `hexo s

```bash
$ hexo server
```

* `-p` 选项，指定服务器端口，默认为 4000
* `-i` 选项，指定服务器 IP 地址，默认为 0.0.0.0
* `-s` 选项，静态模式 ，仅提供 public 文件夹中的文件并禁用文件监视

**说明** ：运行服务器前需要安装 hexo-server 插件

```bash
$ npm install hexo-server --save
```

### 上传到远程仓库

hexo deploy` 命令用于部署网站，一般可以简写为 `hexo d

```bash
$ hexo deploy
```

* `-g` 选项，指定生成后部署，与 `hexo g -d` 等价

**说明** ：部署前需要修改 _config.yml 配置文件，下面以 git 为例进行说明

```yaml
deploy:
    type: git
    repo: <repository url>
    branch: master
    message: 自定义提交消息，默认为Site updated: {{ now('YYYY-MM-DD HH:mm:ss') }}
```

### 显示hexo版本

~~~bash
$ hexo version
~~~

 显示 Hexo 版本。 

> 欢迎各位小伙伴在下方留言讨论,发表你们的诉求,争取把这个博客环境搭建成一个爱学习,爱讨论的微社区,让我们一起进步,一起学习

