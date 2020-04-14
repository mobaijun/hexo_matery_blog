---
title: 解决Tomcat9中文乱码
author: 框架师|墨白
img: 
coverImg: 
top: false
abbrlink: 3475992966
cover: true
toc: true
mathjax: false
summary: 
tags:
  - Tomcat
categories:
  - IDEA
date: 2019-12-12 11:32:03
password:
---

##### 刚下载的tomcat9解压完成启动以后发现输出中文乱码,如下:

<table>
    <tr>
       <img
          src="https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/tuchuang/1.png"></td>
    </tr>
</table>

 startup.bat启动时乱码：

## 解决方法

打开“/apache-tomcat-9.0.29/conf/logging.properties”文件

<table>
    <tr>
       <img
          src="https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/tuchuang/2.png"></td>
    </tr>
</table>

修改编码格式: 

把java.util.logging.ConsoleHandler.encoding = UTF-8改成java.util.logging.ConsoleHandler.encoding = GBK 

<table>
    <tr>
       <img
          src="https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/tuchuang/3.png"></td>
    </tr>
</table>

~~~java
java.util.logging.ConsoleHandler.encoding = GBK
~~~
修改完重新启动tomcat,乱码解决:

<table>
    <tr>
       <img
          src="https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/tuchuang/4.png"></td>
    </tr>
</table>

**持续更新中...，如果遇到问题欢迎联系我，在文章最后评论区【留言和讨论】，当然，欢迎点击文章最后的打赏按键，请墨白喝一杯冰阔乐，笑～**

<escspe>

<table>
    <tr>
        <td><img width="150px" height="150px"
                 src="https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/zf/alipay.jpg"></td>
        <td><img width="150px" height="150px"
                 src="https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/zf/wechat.jpg"></td>
        <td><img width="150px" height="150px"
                 src="https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/zf/zan.jpg"></td>
    </tr>
</table>

<escape>

