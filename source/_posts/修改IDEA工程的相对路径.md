---
title: 修改IDEA工程的相对路径
author: 墨白
img: 
coverImg: 
top: false
abbrlink: 515350045
cover: false
toc: true
mathjax: false
tags:
  - IDEA
categories:
  - IDEA
date: 2019-12-19 14:45:41
password:
summary:
---

* 修改IDEA工程相对路径,代码如下

~~~java
package com.mobaijun.day03;

import java.io.File;
import java.util.Properties;
import java.util.Set;

/**
 * @Author: Auser·杰
 * Development: IntelliJ IDEA 2018.2.4 x64
 * ClassName: Demo06
 * ClassCreateDate: 2019/12/19 14:40
 * 类简介: 修改IDEA相对路径
 */
public class Demo06 {
    public static void main(String[] args) {
        // Properties保存了我们Java程序运行的时候的一些信息
        // Properties就是Map集合
        Properties p = System.getProperties();
        // 遍历properites
        // 键找值
        // 1.获取所有的键
        Set<String> keys = p.stringPropertyNames();
        // 2.遍历获取每个键
        for (String key : keys) {
            // 3.通过键找到值
            String value = p.getProperty(key);
            System.out.println(key + "::" + value);
        }
        // 修改idea的相对路径
        System.setProperty("user.dir", "F:\\IdeaProjects");
        // idea的相对路径是工程路径,可以修改
        File file = new File("");
        System.out.println("file = " + file.getAbsolutePath());
    }
}
~~~

