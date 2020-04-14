---
title: 'IntelliJ IDEA 插件,用了上头的那种'
author: 墨白
img: 
coverImg: 
top: false
cover: false
abbrlink: 496658187
toc: true
mathjax: false
tags:
  - IDEA
  - JRebel
categories:
  - IDEA
date: 2019-12-20 11:27:51
password:
summary:
---

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2019-12-21/1.jpg)

* 引言:

* 你在写项目的时候会不会因为每修改一行代码就要重新启动项目而觉得烦恼,我在没有遇到JRebel的时候就很烦恼,重启项目如果电脑配置还可以的话就不怎么耗时,反之,心里苦撒,今天给大家推荐一款IDEA热部署插件,下面看正文;

**热部署:就是在应用正在运行的时候升级软件，却不需要重新启动应用。**

* 今天给大家推荐的这款插件是JRebel,JRebel是一套JavaEE开发工具。JRebel允许开发团队在有限的时间内完成更多的任务修正更多的问题，发布更高质量的软件产品。JRebel是收费软件，用户可以在JRebel官方站点下载30天的评估版本。

* Jrebel 可快速实现热部署，节省了大量重启时间，提高了个人开发效率。JRebel是一款JAVA虚拟机插件，它使得JAVA程序员能在不进行重部署的情况下，即时看到代码的改变对一个应用程序带来的影响。JRebel使你能即时分别看到代码、类和资源的变化，你可以一个个地上传而不是一次性全部部署。当程序员在开发环境中对任何一个类或者资源作出修改的时候，这个变化会直接反应在部署好的应用程序上，从而跳过了构建和部署的过程，每年可以省去部署用的时间花费高达5.25个星期。以上摘自百度百科,可以看到这款插件评价还是很高的;

* 测试版本:

| IDEA版本   | IntelliJ IDEA 2018.2.4 x64 |
| ---------- | -------------------------- |
| JRebel版本 | 2019.2.2                   |

下面先来安装

我这里就用最简单最方便的方式来安装它了,点击File==>Settings==>Plugins,搜索JRebel,点击install安装重启就可以了,因为我已经安装过了就不是install了

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2019-12-21/2.jpg)

因为JRebel是付费的,所以重启之后打开这个小DeBug进行激活

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2019-12-21/3.jpg)

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2019-12-21/4.jpg)

 首先我是赞同有小金库的玩家进行付费使用,点进这个页面以后输入本地IP地址,但是暂时还无法激活,我们还需要两个步骤,打开这个链接 

~~~xml
https://github.com/ilanyu/ReverseProxy/releases/tag/v1.4
~~~

下载更改DNS服务器的工具

根据自己的电脑下载相应版本,我电脑是64位的,所以我下载的也是64位的

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2019-12-21/5.jpg)

下载完成以后直接双击打开出现如下界面,在激活成功以后才可以关闭

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2019-12-21/6.jpg)

 现在就暂时不用了,不要关闭,不要关闭,不要关闭,换个网址拿激活码ID 

~~~xml
地址:https://www.qvdv.com/tools/qvdv-guid.html
~~~

进入这个网址复制下面红色框以内的文字

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2019-12-21/7.jpg)

回到IDEA这个位置,复制生成的GUID,在下面输入你的本地ID地址和GUID进行激活

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2019-12-21/8.jpg)

出现以下界面就是激活成功了

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2019-12-21/9.jpg)

如果以上都不成功也无妨,打开下面这个链接,直接复制粘贴🆗:

  ~~~xml
https://jrebel.qekang.com/
  ~~~

 在激活页面相应位置输入我下图打红色框的位置即可,这种最简单用的别人的服务器地址,但是也不稳定,上面的比较麻烦但是很稳定 

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2019-12-21/10.jpg)

* 再推荐几个IDEA插件:J2EEcfgFile

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2019-12-21/11.jpg)

一键生成以下你需要的模板,你只需要更改相关参数和路径即可:

* web.xml 
* db.properties 
* mybatis-config.xml 
* XxxMapper.xml 
* applicationContext-mapper.xml 
* springmvc.xml 
* applicationContext-redis.xml 
* applicationContext-shiro.xml 
* applicationContext-activemq.xml 
* applicationContext-rocketmq.xml 
* applicationContext-elasticsearch.xml 
* log4j.properties 
* log4j2.xml



* SSMCodeGen

一键将Java-maven普通项目转换成web项目

下面是两个插件都下载安装完成以后的效果

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2019-12-21/12.jpg)

生成成功可以看到有提示

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2019-12-21/13.jpg)

 生成成功以后我们可以看到,相对应的applicationContext-mapper.xml文件和内容已经生成成功了,我们只需要修改下相关配置,当然,我上面列的那些文件都可以一键生成,这个是某培训机构的老师开发的,目前已经上架了IDEA插件市场,你只需要下载安装即可 

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2019-12-21/14.jpg)

applicationContext-mapper.xml,其他的配置文件根据自己的需求测试使用

  ~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:tx="http://www.springframework.org/schema/tx"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd
       http://www.springframework.org/schema/tx
       http://www.springframework.org/schema/tx/spring-tx.xsd
       http://www.springframework.org/schema/context
       http://www.springframework.org/schema/context/spring-context.xsd">

    <!-- 加载属性文件 -->
    <context:property-placeholder location="classpath:db.properties"/>

    <!-- 配置数据源 -->
    <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource"
          destroy-method="close">
        <property name="url" value="${jdbc.url}" />
        <property name="username" value="${jdbc.username}"/>
        <property name="password" value="${jdbc.password}"/>
        <property name="driverClassName" value="${jdbc.driver}"/>
        <property name="maxActive" value="${jdbc.maxActive}"/>
        <property name="minIdle" value="${jdbc.minIdle}"/>
    </bean>

    <!-- 配置SqlSessionFactory -->
    <bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
        <!-- 设置数据源 -->
        <property name="dataSource" ref="dataSource"/>
        <!-- 设置类型别名 (采用包扫描) -->
        <property name="typeAliasesPackage" value="com.xxx.pojo"/>
        <!-- 设置mybatis-config.xml -->
        <property name="configLocation" value="classpath:mybatis-config.xml"/>
        <!-- 设置SQL映射文件
        <property name="mapperLocations" value="classpath:mappers/**/*.xml"/>
         -->
    </bean>

    <!-- 配置数据访问接口的代理对象 (批量配置)
        到基础包下扫描所有的数据访问接口，再创建它们的代理对象，然后交给Spring容器
        bean的id: 默认为接口的类名，首字母小写
    -->
    <bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">
        <property name="basePackage" value="com.xxx.mapper"/>
    </bean>

    <!-- 配置数据源事务管理器(DataSourceTransactionManager) -->
    <bean id="transactionManager"
          class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
        <property name="dataSource" ref="dataSource"/>
    </bean>

    <!-- 配置开启事务注解驱动 -->
    <tx:annotation-driven />

</beans>
  ~~~

下面说下SSMCodeGen这个插件,和上面那个是配套使用的,同样来自某培训机构,它可以一键将你的普通maven项目变成maven-web项目,

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2019-12-21/15.jpg)

转换成功一样有提示:

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2019-12-21/16.jpg)

下图可以看到我们一键从一个maven普通项目转成了maven-web项目了

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2019-12-21/17.jpg)

以上两个插件墨白亲测好使,真心好使,非广告,在推荐一个mybatis插件,这个插件我在博客放了教程,MyBatisCodeHelper-Pro感兴趣的小伙伴点击文末进入我的博客,查看mybatis插件的教程;

重启插件:

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2019-12-21/18.jpg)

下载IDEA Restart:

![](https://wang_lianjie.gitee.io/mobai_images.gitee.io/img/2019-12-21/19.jpg)

评语:好使

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

