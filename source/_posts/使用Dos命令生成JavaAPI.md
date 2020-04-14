---
title: 使用Dos命令生成JavaAPI
author: 墨白
top: false
cover: false
toc: true
mathjax: false
tags:
  - Dos
categories:
  - Java
abbrlink: 145914589
date: 2020-03-27 15:41:20
img:
coverImg:
password:
summary:
---



> 我们知道在Java语言中有三种注释,分别是单行注释,多行注释和文档注释,其中文档注释是可以将注释生成API文档的,下面就来看一下如何将文档注释生成API

新建一个`Test.java`文件,键入一下内容

~~~java
package com.mobaijun.test1;
/**
 * @Author: Auser·杰
 * Development: IntelliJ IDEA 2018.2.4 x64
 * ClassName: Test
 * ClassCreateDate: 2020/3/27 14:52
 * 类简介: 测试类
 */
public class Test {
    /**
     * Author: Auser·杰
     * MethodName: main
     * MethodCreateDate: 2020/3/27 14:53
     * Return: void
     * Param: [args]
     * 方法说明: main开始运行程序
     */
    public static void main(String[] args) {
        String str = "世界你好";
        System.out.println("str = " + str);
    }
}
~~~

进入文件硬盘目录,启动程序

![地址栏输入cmd]( https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2020-03-27/1.jpg )

输入以下命令

~~~bash
javadoc -charset gbk Test.java
~~~

可以看到命令行输出的内容,显示正在编译相关文档

![正在编译内容]( https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2020-03-27/2.jpg )

然后我们编译完成会在硬盘目录看到很多html文件,选择那个类名一样的文件打开即可,这个就是我们编译过后的API文档了,点击打开看一下效果

![编译完成]( https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2020-03-27/3.jpg )

文档中有一部分乱码,可能是notepad++编码和命令行编码出现冲突,使用IDEA编写的代码和notepad++所使用的编码是不一样的,需要自行去修改编码,上面那行命令也可以改为UTF-8;

![有部分乱码]( https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2020-03-27/4.jpg )

