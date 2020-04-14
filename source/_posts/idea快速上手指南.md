---
title: Idea快速入门指南
author: 墨白
img: 
coverImg: 
top: false
cover: false
abbrlink: 3819560515
toc: true
mathjax: false
tags:
  - 其他
categories:
  - IDEA
date: 2019-12-21 12:00:09
password:
summary:
---
# Idea快速入门指南

## 1.安装

### 1.1.安装

网上下载最新的IDEA版本2017.3.4版本：

 ![]( https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/1.png )

双击打开，

 ![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/2.png)

选择一个目录，最好不要中文和空格：

 ![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/3.png)

然后选择桌面快捷方式，请选择64位：

 ![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/4.png)

然后选择安装：

 ![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/5.png)

开始安装：

 ![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/6.png)

然后勾选安装后运行，Finish：

 ![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/7.png)



### 1.2.首次配置

 ![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/8.png)

然后是UI界面选择，有白色和黑色两款，总有一款适合你：

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/9.png)

把不需要的组件禁用：

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/10.png)

插件暂时不选择安装，以后有需求还可以来安装：

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/11.png)

然后进入运行界面：

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/12.png)

激活Idea：

 ![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/13.png)

这里有三种激活方式：

- 第一种:购买正版用户(如果有资金最好选择正版)
- 第二种:激活码(这种方法在下面有讲解)
- 第三种:在线激活(有一个过期时间，这个时间一过就必须再次联网授权服务器请求激活)

土豪请选择第一种，每年大概不到$700

非土豪，请参考：http://idea.lanyus.com/   中的教程。



激活完成，就可以开始撸代码了：

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/14.png)

## 2.配置

我们在启动界面打开配置页面：

 ![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/15.png)

进入idea以后，我们可以进行一系列配置。

### 2.1.字体和主题：

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/16.png)

另外，主题也可以到网上下载，但是建议大家不要去浪费时间了。

### 2.2.启动项：

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/17.png)



### 2.3.快捷键

类名自动补全：

默认并不是Alt + /。而大家玩eclipse比较熟悉了，所以我们改成Alt + /

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/18.png)

代码生成：

默认的代码生成快捷键：`Alt + insert`。很多朋友电脑中没有 Insert 按键。

因此这里需要修改，大家自己选择。我设置的是`Alt + I`

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/19.png)



还有快捷弹出 New菜单：

默认是`Alt+Insert`，没有`Insert`按键的同学，可以修改。我设置的也是`Alt+ I`

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/55555.png)

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/20.png)



### 2.4.代码联想

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/21.png)



### 2.5.编辑器字体：

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/22.png)



### 2.6.编码

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/23.png)

### 2.7.maven

idea自带的maven版本是3.3.9，我们一般不需要指定自己的。不过我们可以指定settings.xml来修改自己的仓库地址。

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/24.png)



### 2.8.ES6语法支持

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/25.png)

### 2.9.Vue插件安装

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/26.png)



## 3.常用快捷键

|        快捷键        |                          作用                           |
| :------------------: | :-----------------------------------------------------: |
|       Ctrl + Y       |                        删除一行                         |
|       Ctrl + D       |                        复制一行                         |
|    Ctrl + Alt + L    |                         格式化                          |
|    Ctrl + Alt + O    |                          导包                           |
| Alt+Insert（可修改） | New菜单\代码生成菜单（生成getter和setter，maven依赖等） |
|       Ctrl + /       |                          注释                           |
|   Ctrl + Shift + /   |                        多行注释                         |
|  Ctrl + Alt + 左/右  |    回退到上一次操作的地方，等于eclipse中的 Alt+左/右    |
| Shift + Alt + 上/下  |                  将代码上移或下移一行                   |

Ctry + H ：罗列类的继承关系





## 4.代码补全

idea有很多的代码自动补全功能，有两个地方可以设置：

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/27.png)

还有一个：

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/28.png)

其作用演示：

 ![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/idea演示.gif)



通过后缀的方式快速完成一些代码的补全，一般写完后缀，按tab或回车即可。罗列一些比较常用的：

| 代码 |            效果            |
| :--: | :------------------------: |
| psvm |      自动生成main函数      |
| .var |     自动为对象生成声明     |
| sout | 输出：System.out.println() |
| .if  |         生成if判断         |
| .for |  生成循环，默认是高级for   |
| fori |     用普通for进行遍历      |
| .try |     生成try ... catch      |
|      |                            |
|      |                            |

## 5.project与module

### 5.1.idea的maven理念

在Idea中，没有工作空间的概念，每一个Project就是一个独立的文件夹，也是一个独立的窗口。然后我们可以在Project中创建多个Module。

是不是感觉与maven的项目结构完全一致？

说对了，idea就是完全贯彻了maven的理念。

### 5.2.小技巧

熟悉eclipse的同学会觉得很不方便，无法在一个界面中创建很多的工程。

不过有一个取巧的办法：我们可以创建一个empty的工程：

 ![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/29.png)

然后选择empty工程：

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/30.png)

然后填写名称：

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/31.png)

点击Finish：

 ![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/32.png)

但是接下来，就不要再新建Project了，而是新建Module，Module就类似原来的工程的概念：

 ![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/33.png)

然后创建一个maven工程：

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/34.png)



然后填写项目信息：

 ![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/35.png)



填写项目位置信息：

 ![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/36.png)



界面结构：

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/37.png)





## 6.打开springboot的run dashboard

先看下run dashboard是什么：

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/38.png) 

可以看到，这里可以同时显示多个springboot项目，非常方便。



默认情况下，idea的run dashboard是关闭的，当检测到你有多个springboot项目时会弹出提示框，询问是否打开。



如果我们想要自己打开，需要修改配置。

在你的idea的项目目录中，有一个.idea目录：

 ![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/39.png)

其中，有一个workspace.xml：

 ![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/40.png)



打开，搜索Rundashboard，找到下面这段：

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/assets/41.png) 

然后在Component中添加下面的内容：

```xml
<option name="configurationTypes">  
    <set>  
        <option value="SpringBootApplicationConfigurationType" />  
    </set>  
</option> 
```





