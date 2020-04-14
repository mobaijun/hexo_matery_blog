---
title: IOC容器入门案例
author: 墨白
img: 
coverImg: 
top: false
cover: false
toc: true
mathjax: false
tags:
  - 框架
  - Java
categories:
  - 随笔
abbrlink: 3364913315
date: 2020-01-03 14:38:17
password:
summary:
---

## IOC容器入门案例

* 创建maven项目,导入坐标

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
         http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.mobaijun</groupId>
    <artifactId>spring_mvc</artifactId>
    <version>1.0-SNAPSHOT</version>

    <dependencies>
        <!-- spring的IOC坐标 -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
            <version>5.0.2.RELEASE</version>
        </dependency>
        <!--导入junit测试-->
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
        </dependency>
    </dependencies>
</project>
~~~

* 创建User对象

~~~java
package com.mobaijun;

/**
 * @Author: Auser·杰
 * Development: IntelliJ IDEA 2018.2.4 x64
 * ClassName: User
 * ClassCreateDate: 2020/1/3 14:15
 * 类简介:
 */
public class User {

    public User() {
        System.out.println("创建了User对象!");
    }
}
~~~

* `resource`目录下新建application.xml文件

![快捷新建spring配置文件](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/14.42/1.jpg)

* 编写xml配置文件

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd">
    <!-- 创建User对象 -->
    <!--
       id: 对象的别名，用于获取对象
       class: 需要创建的对象，必须是类的全限定名
     -->
    <bean id="user" class="com.mobaijun.User"/>
    <bean id="user2" class="com.mobaijun.User2"/>
    <bean id="user3" class="com.mobaijun.User3"/>
</beans>
~~~

* test目录下新建Demo测试类

~~~java
package com.mobaijun;

import org.junit.Test;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

/**
 * @Author: Auser·杰
 * Development: IntelliJ IDEA 2018.2.4 x64
 * ClassName: Demo1
 * ClassCreateDate: 2020/1/3 14:17
 * 类简介:
 */
public class Demo1 {

    @Test
    public void test1() {
        // 创建IOC容器(模拟beanFactory)
        ApplicationContext ac = new ClassPathXmlApplicationContext("bean.xml");
        User user = (User) ac.getBean("user");
        System.out.println("user = " + user);
    }


    @Test
    public void test2() {
        ApplicationContext ac = new ClassPathXmlApplicationContext("bean.xml");
        User2 user2 = (User2) ac.getBean("user2");
        System.out.println("user2 = " + user2);
    }

    @Test
    public void test3() {
        ApplicationContext ac = new ClassPathXmlApplicationContext("bean.xml");
        User3 user3 = (User3) ac.getBean("user3");
        System.out.println("user3 = " + user3);
    }
}
~~~

> 小结:
>
> 创建项目，导入spring-context坐标
>
> 2）创建User对象
>
> 3）创建bean.xml，定义<bean id="xx" class="xxxx"/>
>
> 4）创建IOC容器（ApplicationContext），从容器获取对象getBean("id")

