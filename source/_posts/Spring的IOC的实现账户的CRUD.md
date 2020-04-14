---
title: Spring的IOC的实现账户的CRUD
author: 墨白
img: 
coverImg: 
top: false
cover: false
toc: true
mathjax: false
tags:
  - 框架
categories:
  - Java
abbrlink: 1185366497
date: 2020-01-03 15:39:21
password:
summary:
---

## Spring的IOC的实现账户的CRUD

> 完整目录结构
>
> ![]( https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/14.42/2.jpg )

* 打开你的图形化界面工具(`sqlyog,navicat...`),创建数据库`spring-test`,导入以下SQL

~~~sql
DROP TABLE IF EXISTS USER;

CREATE TABLE USER (
  id INT(11) NOT NULL AUTO_INCREMENT,
  username VARCHAR(32) NOT NULL COMMENT '用户名称',
  birthday DATETIME DEFAULT NULL COMMENT '生日',
  sex CHAR(1) DEFAULT NULL COMMENT '性别',
  address VARCHAR(256) DEFAULT NULL COMMENT '地址',
  PRIMARY KEY  (id)
) ENGINE=INNODB DEFAULT CHARSET=utf8;


INSERT  INTO USER(id,username,birthday,sex,address) VALUES (41,'老王','2018-02-27 17:47:08','男','北京'),(42,'小二王','2018-03-02 15:09:37','女','北京金燕龙'),(43,'小二王','2018-03-04 11:34:34','女','北京金燕龙'),(45,'艾玛','2018-03-04 12:04:06','男','北京金燕龙'),(46,'老王','2018-03-07 17:37:26','男','北京'),(48,'小马宝莉','2018-03-08 11:44:00','女','北京修正');


DROP TABLE IF EXISTS account;
CREATE TABLE account (
  accountId INT(11) NOT NULL AUTO_INCREMENT,
  UID INT(11) DEFAULT NULL COMMENT '用户编号',
  MONEY DOUBLE DEFAULT NULL COMMENT '金额',
  PRIMARY KEY  (accountId),
  KEY FK_Reference_8 (UID),
  CONSTRAINT FK_Reference_8 FOREIGN KEY (UID) REFERENCES USER (id)
) ENGINE=INNODB DEFAULT CHARSET=utf8;


INSERT  INTO account(accountId,UID,MONEY) VALUES (1,46,1000),(2,45,1000),(3,46,2000);
~~~

* 建表后效果如图

![]( https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/14.42/3.jpg )

* 打开你的IDEA,创建maven项目,导入相关坐标

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.mobaijun</groupId>
    <artifactId>spring_crud</artifactId>
    <version>1.0-SNAPSHOT</version>

    <dependencies>
        <!--数据库驱动-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>5.1.46</version>
        </dependency>
        <!--数据源-->
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>druid</artifactId>
            <version>1.1.6</version>
        </dependency>
        <!-- Spring的JdbcTemplate -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-jdbc</artifactId>
            <version>5.1.10.RELEASE</version>
        </dependency>
        <!--IOC容器-->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
            <version>5.2.1.RELEASE</version>
        </dependency>
        <!--junit测试-->
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
        </dependency>
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <version>1.18.10</version>
        </dependency>
    </dependencies>
</project>
~~~

* 编写Account实体

~~~java
package com.mobaijun.pojo.account;

import lombok.Data;

import java.io.Serializable;

/**
 * @Author: Auser·杰
 * Development: IntelliJ IDEA 2018.2.4 x64
 * ClassName: Account
 * ClassCreateDate: 2020/1/3 14:58
 * 类简介:
 */
@Data
public class Account implements Serializable {

    private int accountId;

    private int uid;

    private double money;
}
~~~

* 编写Dao接口

~~~java
package com.mobaijun.dao.account;

import com.mobaijun.pojo.account.Account;

import java.util.List;

/**
 * @Author: Auser·杰
 * Development: IntelliJ IDEA 2018.2.4 x64
 * InterfaceName: AccountDao
 * InterfaceCreateDate: 2020/1/3 15:02
 * 接口简介:
 */
public interface AccountDao {

    void save(Account account);

    void update(Account account);

    void delete(int accountId);

    List<Account> findAll();
}
~~~

* dao实现

~~~java
package com.mobaijun.dao.account.impl;

import com.mobaijun.dao.account.AccountDao;
import com.mobaijun.pojo.account.Account;
import org.springframework.jdbc.core.BeanPropertyRowMapper;
import org.springframework.jdbc.core.JdbcTemplate;

import java.util.List;

/**
 * @Author: Auser·杰
 * Development: IntelliJ IDEA 2018.2.4 x64
 * ClassName: AccountDaompl
 * ClassCreateDate: 2020/1/3 15:14
 * 类简介:
 */
public class AccountDaompl implements AccountDao {

    // 注入JdbcTemplate
    private JdbcTemplate jdbcTemplate;

    /**
     * Author: Auser·杰
     * MethodName: setJdbcTemplate
     * MethodCreateDate: 2020/1/3 15:05
     * Return: void
     * Param: [jdbcTemplate]
     * 方法说明: 提供setter方法,以便IOC依赖注入
     */
    public void setJdbcTemplate(JdbcTemplate jdbcTemplate) {
        this.jdbcTemplate = jdbcTemplate;
    }

    /**
     * Author: Auser·杰
     * MethodName: save
     * MethodCreateDate: 2020/1/3 15:06
     * Return: void
     * Param: [account]
     * 方法说明: 修改并保存
     */
    public void save(Account account) {
        jdbcTemplate.update("insert into account(uid,money) values(?,?)"
                , account.getUid(), account.getMoney());
    }

    /**
     * Author: Auser·杰
     * MethodName: update
     * MethodCreateDate: 2020/1/3 15:09
     * Return: void
     * Param: [account]
     * 方法说明:更新
     */
    public void update(Account account) {
        jdbcTemplate.update("update account set uid=?,money=? where accountId=?"
                , account.getUid(), account.getMoney(), account.getAccountId());
    }

    /**
     * Author: Auser·杰
     * MethodName: delete
     * MethodCreateDate: 2020/1/3 15:10
     * Return: void
     * Param: [accountId]
     * 方法说明: 根据ID删除
     */
    public void delete(int accountId) {
        jdbcTemplate.update("delete from account where accountId = ?", accountId);
    }

    /**
     * Author: Auser·杰
     * MethodName: findAll
     * MethodCreateDate: 2020/1/3 15:10
     * Return: java.util.List<com.mobaijun.pojo.account.Account>
     * Param: []
     * 方法说明: 查询全部
     */
    public List<Account> findAll() {
        return jdbcTemplate.query("select * from account",
                new BeanPropertyRowMapper<Account>(Account.class));
    }
}
~~~

* accountService接口

~~~java
package com.mobaijun.service;

import com.mobaijun.pojo.account.Account;

import java.util.List;

/**
 * @Author: Auser·杰
 * Development: IntelliJ IDEA 2018.2.4 x64
 * InterfaceName: AccountService
 * InterfaceCreateDate: 2020/1/3 15:16
 * 接口简介:account接口
 */
public interface AccountService {

    void save(Account account);

    void update(Account account);

    void delete(int accountId);

    List<Account> findAll();
}
~~~

* accountServiceImpl实现

~~~java
package com.mobaijun.service.impl;

import com.mobaijun.dao.account.AccountDao;
import com.mobaijun.pojo.account.Account;
import com.mobaijun.service.AccountService;

import java.util.List;

/**
 * @Author: Auser·杰
 * Development: IntelliJ IDEA 2018.2.4 x64
 * ClassName: AccountServiceImpl
 * ClassCreateDate: 2020/1/3 15:03
 * 类简介:
 */
public class AccountServiceImpl implements AccountService {

    // 注入dao接口
    private AccountDao accountDao;

    /**
     * Author: Auser·杰
     * MethodName: setAccountDao
     * MethodCreateDate: 2020/1/3 15:18
     * Return: void
     * Param: [accountDao]
     * 方法说明: 给IOC进行依赖注入
     */
    public void setAccountDao(AccountDao accountDao) {
        this.accountDao = accountDao;
    }

    /**
     * Author: Auser·杰
     * MethodName: save
     * MethodCreateDate: 2020/1/3 15:18
     * Return: void
     * Param: [account]
     * 方法说明: 保存
     */
    public void save(Account account) {
        accountDao.save(account);
    }

    /**
     * Author: Auser·杰
     * MethodName: update
     * MethodCreateDate: 2020/1/3 15:18
     * Return: void
     * Param: [account]
     * 方法说明: 更新
     */
    public void update(Account account) {
        accountDao.update(account);
    }

    /**
     * Author: Auser·杰
     * MethodName: delete
     * MethodCreateDate: 2020/1/3 15:18
     * Return: void
     * Param: [accountId]
     * 方法说明: 删除
     */
    public void delete(int accountId) {
        accountDao.delete(accountId);
    }

    /**
     * Author: Auser·杰
     * MethodName: findAll
     * MethodCreateDate: 2020/1/3 15:18
     * Return: java.util.List<com.mobaijun.pojo.account.Account>
     * Param: []
     * 方法说明: 查询全部
     */
    public List<Account> findAll() {
        return accountDao.findAll();
    }
}
~~~

* jdbc.properties配置文件

~~~properties
jdbc.driver=com.mysql.jdbc.Driver
jdbc.url=jdbc:mysql://localhost:3306/test?characterEncoding=utf-8
jdbc.username=xxxxxx
jdbc.password=xxxxxxx
~~~

* applicationContext-dao.xml配置文件

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd
       http://www.springframework.org/schema/context
       https://www.springframework.org/schema/context/spring-context.xsd">

    <!--扫描数据库配置文件
        classpath: 从类路径下面开始加载
    -->
    <context:property-placeholder location="classpath:db.properties"/>

    <!--创建数据源
        DruidDataSource ds = new DruidDataSource
    -->
    <bean id="dataSources" class="com.alibaba.druid.pool.DruidDataSource">
        <property name="driverClassName" value="${jdbc.driver}"/>
        <property name="url" value="${jdbc.url}"/>
        <property name="username" value="${jdbc.username}"/>
        <property name="password" value="${jdbc.password}"/>
    </bean>

    <!--创建JDBCTemplate对象,注入数据源-->
    <bean id="jdbcTemplate" class="org.springframework.jdbc.core.JdbcTemplate">
        <property name="dataSource" ref="dataSources"/>
    </bean>

    <!--创建dao对象,同时注入JdbcTemplate对象-->
    <bean id="accountDao" class="com.mobaijun.dao.account.impl.AccountDaompl">
        <property name="jdbcTemplate" ref="jdbcTemplate"/>
    </bean>

    <!--创建service对象,同时注入dao对象-->
    <bean id="accountService" class="com.mobaijun.service.impl.AccountServiceImpl">
        <property name="accountDao" ref="accountDao"/>
    </bean>
</beans>
~~~

* test目录下新建test类Demo

~~~java
package com.mobaijun.test;

import com.mobaijun.pojo.account.Account;
import com.mobaijun.service.AccountService;
import org.junit.Test;
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

import java.util.List;

/**
 * @Author: Auser·杰
 * Development: IntelliJ IDEA 2018.2.4 x64
 * ClassName: AccountServiceTest
 * ClassCreateDate: 2020/1/3 15:28
 * 类简介:
 */
public class AccountServiceTest {

    /**
     * Author: Auser·杰
     * MethodName: testFindAl
     * MethodCreateDate: 2020/1/3 15:32
     * Return: void
     * Param: []
     * 方法说明: 查询全部
     */
    @Test
    public void testFindAl() {
        // 创建IOC容器
        ApplicationContext ac = new ClassPathXmlApplicationContext("spring/applicationContext-dao.xml");
        // 获取service对象
        AccountService accountService = (AccountService) ac.getBean("accountService");
        List<Account> list = accountService.findAll();
        /**
         * Author: Auser·杰
         * MethodName: testFindAl
         * MethodCreateDate: 2020/1/3 15:37
         * Return: void
         * Param: []
         * 方法说明: 循环遍历所有数据
         */
        for (Account account : list) {
            System.out.println("account = " + account);
        }
    }

}
~~~

* 结果

![]( https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/14.42/4.jpg )