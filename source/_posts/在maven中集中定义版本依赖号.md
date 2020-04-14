---
title: 在maven集中定义版本依赖号
author: 墨白
img: 
coverImg: 
top: false
abbrlink: 1286498975
cover: false
toc: true
mathjax: false
tags:
  - Maven
categories:
  - IDEA
date: 2019-12-18 10:31:09
password:
summary:
---

### Maven定义依赖版本号

在使用maven构建项目时，一系列的依赖往往需要使用相同的版本号，这时候我们可以在properties标签中定义版本号以便版本管理。


* 在==properties==标签中定义版本

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
         http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.mobaijun</groupId>
    <artifactId>spring_project</artifactId>
    <version>1.0-SNAPSHOT</version>

    <!--集中定义依赖版本号-->
    <properties>
        <spring.version>5.2.1.RELEASE</spring.version>
        <lombok.version>1.18.10</lombok.version>
    </properties>
    
</project>
~~~

* 在=='dependencies'==标签中通过${}引用版本号

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
         http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.mobaijun</groupId>
    <artifactId>spring_project</artifactId>
    <version>1.0-SNAPSHOT</version>

    <!--集中定义依赖版本号-->
    <properties>
        <spring.version>5.2.1.RELEASE</spring.version>
        <lombok.version>1.18.10</lombok.version>
    </properties>

    <!--项目依赖-->
    <dependencies>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-aop</artifactId>
            <version>${spring.version}</version>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
            <version>${spring.version}</version>
        </dependency>
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <version>${lombok.version}</version>
        </dependency>
    </dependencies>
</project>
```

