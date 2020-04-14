---
title: IDEA单行注释快捷键输出空格问题
author: 框架师|墨白
img: 
coverImg: 
top: false
cover: true
abbrlink: 3318988070
toc: true
mathjax: false
summary: 
tags:
  - 其他
categories:
  - IDEA
date: 2019-12-13 14:41:03
password:
---

## 原因

昨天因为重装了系统,配置好了所有环境以后今天刚开始写代码,然后快捷键ctrl + /快捷键注释的时候发现效果是这样的,单行注释直接贴边了,这能忍,网上搜索了一下发现解决方案如下:

~~~java
// 查询全部
	List<User> findAllUser();
~~~

## 解决:

* 打开File===>Settings

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/images/image-1.png)

* 点开Editor=>Code Style=>Java=>Code Generation ==勾选下面截图的位置==

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/images/image-2.png)

返回IDEA重新输入:

~~~java
// 查询全部
List<User> findAll();
~~~

以上就是今天的水文了,欢迎吐槽



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