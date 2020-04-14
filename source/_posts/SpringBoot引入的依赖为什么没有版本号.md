---
title: SpringBoot引入的依赖为什么没有版本号
author: 墨白
img: 
coverImg: 
top: false
abbrlink: 1944509409
cover: false
toc: true
mathjax: false
tags:
  - 框架
categories:
  - Java
date: 2019-12-20 10:12:57
password:
summary:
---

* 在入门springboot的时候我相信很多朋友都有过这样的疑问,为什么spring boot项目在pom文件引入的某些依赖不需要指定版本呢?但是却并不妨碍我们使用或下载jar包

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.mobaijun</groupId>
    <artifactId>spring_mybatis</artifactId>
    <version>1.0-SNAPSHOT</version>
    <!--父项目-->
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.2.1.RELEASE</version>
    </parent>
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
              <!--这个版本号是我自己添加的-->
            <version>2.1.9.RELEASE</version>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-jdbc</artifactId>
            <!--这个版本号是我自己添加的-->
            <version>2.1.9.RELEASE</version>
        </dependency>
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
        </dependency>
    </dependencies>
</project>
~~~

* 在Spring Boot 项目下的pom.xml文件中通常都会有一个标签，用来指定继承的父pom，如下：

```xml
<parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.2.1.RELEASE</version>
    </parent>
```

* 可以点击这个spring-boot-starter-parent依赖进去看看里面发生了什么?

```xml
<?xml version="1.0" encoding="utf-8"?><project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-dependencies</artifactId>
    <version>2.2.1.RELEASE</version>
    <relativePath>../../spring-boot-dependencies</relativePath>
  </parent>
```

* 看到spring-boot-starter-parent也继承了一个pom,在进入spring-boot-dependencies这个依赖我们就可以看到了, 顶级的pom文件的坐标如下，通过标签我们应该知道这个pom文件时用来管理依赖版本号的。 

~~~xml
 <modelVersion>4.0.0</modelVersion>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-dependencies</artifactId>
  <version>2.2.1.RELEASE</version>
  <packaging>pom</packaging>
~~~

* 在这个pom.xml中定义了很多的标签用来管理引入依赖和插件的版本。
  在引入依赖的时候，即使你不指定依赖的版本，Spring Boot 也会通过Maven 的继承关系，引入依赖的版本，从而完成版本的统一。
  另外不是所有依赖都在parent中指定了版本，对于没有指定版本的依赖依然需要手动指定版本否则会出现No version of dendency的异常
  当然你也可以不使用Maven继承的依赖版本，只需要在引入依赖的时候指定具体的依赖版本即可。 

