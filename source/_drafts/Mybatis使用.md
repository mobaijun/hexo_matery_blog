---
abbrlink: 84dec666
---
# Mybatis Plus使用

[课程地址](https://www.imooc.com/video/19490)

### 技术储备

spring 

mybatis

maven

spring boot

IDEA

jdk1.8

### mybatis 和 JPA

mybatis优势

* sql语句可以自由控制,灵活,性能较高

* SQL和代码分离,易于阅读和维护

* 提供xml标签,支持编写动态sql

#### 劣势

* 简单的crud也需要写sql代码
* xml中大量sql需要维护
* mybatis功能很少,但支持plugin

### JPA优势

* jpa移植性较好
* 提供了很多crud方法,无需编写sql,开发效率高
* 对象化成都更高

## mybatis -plus简介

mybatis-plus是一个mybatis的增强工具,在mybatis原有的功能上做增强不做修改

![image-20191223141334800](F:%5Cmobai_images.gitee.io%5Cimg%5Chexocoding%5Cimage-20191223141334800.png)

[Mybatis-Plus官网]( https://mp.baomidou.com/ )

#### 特性

* 无侵入(只做增强,不做修改),损耗小,强大的crud操作
* 支持lambda表达式,支持多种数据库
* 支持主键自动生成,支持ActiveRecord模式
* 支持自定义全局通用操作,支持关键词自动转义
* 内置代码生成器,内置分页插件,内置性能分析插件
* 内置全局拦截插件,内置sql剥离器

 