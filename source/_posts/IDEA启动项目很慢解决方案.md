---
title: IDEA启动项目很慢解决方案
author: 墨白
img: 
coverImg: 
top: false
abbrlink: 3587260547
cover: false
toc: true
mathjax: false
tags:
  - IDEA
  - null
categories:
  - IDEA
date: 2019-12-19 09:26:54
password:
summary:
---

### IDEA启动项目加载很慢解决方案

* Interllij IDEA由于功能很多，又注重搜索与只能提示的速度，启动时把很多数据提前加载到内存里面，导致启动特别慢。

  即使优化到极致，Interllij IDEA的启动速度也不会改善太多，但还是能够减少一些启动时间的，下面详细介绍。

* IDEA默认的JVM设置，已经不适合大多数人。默认的xmx只分配了750兆，很容易用完导致不停垃圾回收从而卡顿。

  如果你IDEA的东西多了，甚至启动时就由于内存用完开始频繁垃圾回收导致软件运行速度变慢影响启动时间了。

  为了设置JVM参数，我们先找到IDEA的安装目录。

  对IDEA的快捷方式点右键，打开所在文件夹。

![image](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2019-12-19/1.jpg)

 2个最重要的必须改Xmx与Xms ,修改你的IDEA内存参数:**idea64.exe.vmoptions**,把它们改的大一点，并且一样大。

一样大可以使IDEA启动时初始堆内存就直接到最大，以免中途扩容影响启动速度。

具体多大取决于你的内存大小，例如你有8G内存可以给IDEA分配2G~3G使用。

如果是32位的系统，那么只能用32位的IDEA了，这时最多只能分配1.4~1.5G左右。

~~~xml
-Xms2048m
-Xmx2048m
-XX:ReservedCodeCacheSize=240m
-XX:+UseConcMarkSweepGC
-XX:SoftRefLRUPolicyMSPerMB=50
-ea
-Dsun.io.useCanonCaches=false
-Djava.net.preferIPv4Stack=true
-Djdk.http.auth.tunneling.disabledSchemes=""
-XX:+HeapDumpOnOutOfMemoryError
-XX:-OmitStackTraceInFastThrow

~~~

* **idea.exe.vmoptions**

~~~xml
-server
-Xms2048m
-Xmx2048m
-XX:ReservedCodeCacheSize=240m
-XX:+UseConcMarkSweepGC
-XX:SoftRefLRUPolicyMSPerMB=50
-ea
-Dsun.io.useCanonCaches=false
-Djava.net.preferIPv4Stack=true
-Djdk.http.auth.tunneling.disabledSchemes=""
-XX:+HeapDumpOnOutOfMemoryError
-XX:-OmitStackTraceInFastThrow
~~~

以上就是今天上午的随笔了,欢迎讨论