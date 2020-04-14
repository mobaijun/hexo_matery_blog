---
title: SSM框架面试题精选
author: 墨白
top: true
cover: false
toc: true
mathjax: false
tags:
  - 框架
  - null
categories:
  - 面试题
abbrlink: 1847791471
date: 2020-03-21 15:39:21
img:
coverImg:
password:
summary:
---

# SSM框架面试题

## Spring面试题

###  Spring是什么?

 Spring是一个轻量级的IoC和AOP容器框架。是为Java应用程序提供基础性服务的一套框架，目的是用于简化企业应用程序的开发，它使得开发者只需要关心业务需求。常见的配置方式有三种：基于XML的配置、基于注解的配置、基于Java的配置。

主要由以下几个模块组成：

Spring Core：核心类库，提供IOC服务；

Spring Context：提供框架式的Bean访问方式，以及企业级功能（JNDI、定时任务等）；

Spring AOP：AOP服务；

Spring DAO：对JDBC的抽象，简化了数据访问异常的处理；

Spring ORM：对现有的ORM框架的支持；

Spring Web：提供了基本的面向Web的综合特性，例如多方文件上传；

Spring MVC：提供面向Web应用的Model-View-Controller实现。

###  Spring 的优点？

* 轻量：Spring 是轻量的，基本的版本大约2MB。
* 控制反转：Spring通过控制反转实现了松散耦合，对象们给出它们的依赖，而不是创建或查找依赖的对象们。
* 面向切面的编程(AOP)：Spring支持面向切面的编程，并且把应用业务逻辑和系统服务分开。
* 容器：Spring 包含并管理应用中对象的生命周期和配置。
* MVC框架：Spring的WEB框架是个精心设计的框架，是Web框架的一个很好的替代品。
* 事务管理：Spring 提供一个持续的事务管理接口，可以扩展到上至本地事务下至全局事务（JTA）。
* 异常处理：Spring 提供方便的API把具体技术相关的异常（比如由JDBC，Hibernate or JDO抛出的）转化为一致的unchecked 异常。

### Spring 在ssm中起什么作用？

* Spring：轻量级框架

* 作用：Bean工厂，用来管理Bean的生命周期和框架集成。

* 两大核心：

  1、IOC/DI(控制反转/依赖注入) ：把dao依赖注入到service层，service层反转给action层，Spring顶层容器为BeanFactory。

  2、AOP：面向切面编程

### Spring的事务？

* 编程式事务管理：编程方式管理事务，极大灵活性，难维护。 
*  声明式事务管理：可以将业务代码和事务管理分离，用注解和xml配置来管理事务。 

###  介绍一下Spring的事务管理？ 

事务就是对一系列的数据库操作（比如插入多条数据）进行统一的提交或回滚操作，如果插入成功，那么一起成功，如果中间有一条出现异常，那么回滚之前的所有操作。 这样可以防止出现脏数据，防止数据库数据出现问题。 

开发中为了避免这种情况一般都会进行事务管理。Spring中也有自己的事务管理机制，一般是使用TransactionMananger进行管理，可以通过Spring的注入来完成此功能

### IOC 在项目中的作用？

*  作用：Ioc解决对象之间的依赖问题，把所有Bean的依赖关系通过配置文件或注解关联起来，降低了耦合度。 

### Spring的配置文件中的内容？

* 开启事务注解驱动
* 事务管理器
* 开启注解功能，并配置扫描包
* 配置数据库
* 配置SQL会话工厂，别名，映射文件
* 不用编写Dao层的实现类

### Spring下的注解？

* 注册：@Controller @Service @Component
* 注入：@Autowired @Resource
* 请求地址：@RequestMapping
* 返回具体数据类型而非跳转：@ResponseBody

### Spring DI 的三种方式?

*  构造器注入：通过构造方法初始化 
*  setter方法注入：通过setter方法初始化 
*  接口注入 

### 哪种依赖注入方式你建议使用，构造器注入，还是 Setter方法注入？

你两种依赖方式都可以使用，构造器注入和Setter方法注入。最好的解决方案是用构造器参数实现强制依赖，setter方法实现可选依赖。

### Spring主要使用了什么模式？

* 工厂模式：每个Bean的创建通过方法
* 单例模式：默认的每个Bean的作用域都是单例
* 代理模式：关于Aop的实现通过代理模式

### IOC，AOP的实现原理？

* IOC：通过反射机制生成对象注入
* AOP：动态代理

### 解释AOP

面向切面的编程，或AOP， 是一种编程技术，允许程序模块化横向切割关注点，或横切典型的责任划分，如日志和事务管理。

### Aspect 切面

AOP核心就是切面，它将多个类的通用行为封装成可重用的模块，该模块含有一组API提供横切功能。比如，一个日志模块可以被称作日志的AOP切面。根据需求的不同，一个应用程序可以有若干切面。在Spring AOP中，切面通过带有@Aspect注解的类实现。

### 在Spring AOP 中，关注点和横切关注的区别是什么？

关注点是应用中一个模块的行为，一个关注点可能会被定义成一个我们想实现的一个功能。
横切关注点是一个关注点，此关注点是整个应用都会使用的功能，并影响整个应用，比如日志，安全和数据传输，几乎应用的每个模块都需要的功能。因此这些都属于横切关注点。

通知是个在方法执行前或执行后要做的动作，实际上是程序执行时要通过SpringAOP框架触发的代码段。

Spring切面可以应用五种类型的通知：

* before：前置通知，在一个方法执行前被调用。
* after: 在方法执行之后调用的通知，无论方法执行是否成功。
* after-returning: 仅当方法成功完成后执行的通知。
* after-throwing: 在方法抛出异常退出时执行的通知。
* around: 在方法执行之前和之后调用的通知。

###  释Spring Bean的生命周期？

首先说一下Servlet的生命周期：实例化，初始init，接收请求service，销毁destroy；

 Spring上下文中的Bean生命周期也类似，如下：

* 实例化Bean：

对于BeanFactory容器，当客户向容器请求一个尚未初始化的bean时，或初始化bean的时候需要注入另一个尚未初始化的依赖时，容器就会调用createBean进行实例化。对于ApplicationContext容器，当容器启动结束后，通过获取BeanDefinition对象中的信息，实例化所有的bean。

* 设置对象属性（依赖注入）：

实例化后的对象被封装在BeanWrapper对象中，紧接着，Spring根据BeanDefinition中的信息 以及 通过BeanWrapper提供的设置属性的接口完成依赖注入。

* 处理Aware接口：

接着，Spring会检测该对象是否实现了xxxAware接口，并将相关的xxxAware实例注入给Bean：

* 如果这个Bean已经实现了BeanNameAware接口，会调用它实现的setBeanName(String beanId)方法，此处传递的就是Spring配置文件中Bean的id值；

* 如果这个Bean已经实现了BeanFactoryAware接口，会调用它实现的setBeanFactory()方法，传递的是Spring工厂自身。

* 如果这个Bean已经实现了ApplicationContextAware接口，会调用setApplicationContext(ApplicationContext)方法，传入Spring上下文；

* BeanPostProcessor：

如果想对Bean进行一些自定义的处理，那么可以让Bean实现了BeanPostProcessor接口，那将会调用postProcessBeforeInitialization(Object obj, String s)方法。

* InitializingBean 与 init-method：

如果Bean在Spring配置文件中配置了 init-method 属性，则会自动调用其配置的初始化方法。

* 如果这个Bean实现了BeanPostProcessor接口，将会调用postProcessAfterInitialization(Object obj, String s)方法；由于这个方法是在Bean初始化结束时调用的，所以可以被应用于内存或缓存技术；

> 以上几个步骤完成后，Bean就已经被正确创建了，之后就可以使用这个Bean了。

* DisposableBean：

当Bean不再需要时，会经过清理阶段，如果Bean实现了DisposableBean这个接口，会调用其实现的destroy()方法；

* destroy-method：

最后，如果这个Bean的Spring配置中配置了destroy-method属性，会自动调用其配置的销毁方法。

###  解释Spring支持的几种bean的作用域

Spring容器中的bean可以分为5个范围：

* singleton：默认，每个容器中只有一个bean的实例，单例的模式由BeanFactory自身来维护。

* prototype：为每一个bean请求提供一个实例。

* request：为每一个网络请求创建一个实例，在请求完成以后，bean会失效并被垃圾回收器回收。

* session：与request范围类似，确保每个session中有一个bean的实例，在session过期后，bean会随之失效。

* global-session：全局作用域，global-session和Portlet应用相关。当你的应用部署在Portlet容器中工作时，它包含很多portlet。如果你想要声明让所有的portlet共用全局的存储变量的话，那么这全局变量需要存储在global-session中。全局作用域与Servlet中的session作用域效果相同。

### Spring由哪些模块组成?

以下是Spring 框架的基本模块：

* Core module
* Bean module
* Context module
* Expression Language module
* JDBC module
* ORM module
* OXM module
* Java Messaging Service(JMS) module
* Transaction module
* Web module
* Web-Servlet module
* Web-Struts module
* Web-Portlet module

### 核心容器（应用上下文) 模块。

这是基本的Spring模块，提供spring 框架的基础功能，BeanFactory 是任何以spring为基础的应用的核心。Spring 框架建立在此模块之上，它使Spring成为一个容器。

### BeanFactory – BeanFactory 实现举例。

BeanFactory是工厂模式的一个实现，提供了控制反转功能，用来把应用的配置和依赖从真正的应用代码中分离。最常用的BeanFactory 实现是XmlBeanFactory 类。

### 解释JDBC抽象和DAO模块。

通过使用JDBC抽象和DAO模块，保证数据库代码的简洁，并能避免数据库资源错误关闭导致的问题，它在各种不同的数据库的错误信息之上，提供了一个统一的异常访问层。它还利用Spring的AOP 模块给Spring应用中的对象提供事务管理服务。

### 解释对象/关系映射集成模块。

Spring 通过提供ORM模块，支持我们在直接JDBC之上使用一个对象/关系映射映射(ORM)工具，Spring 支持集成主流的ORM框 架，如Hiberate,JDO和 iBATIS SQL Maps。Spring的事务管理同样支持以上所有ORM框架及JDBC。

### 解释WEB 模块

Spring的WEB模块是构建在application context 模块基础之上，提供一个适合web应用的上下文。这个模块也包括支持多 种面向web的任务，如透明地处理多个文件上传请求和程序级请求参数的绑定到你的业务对象。它也有对Jakarta Struts的支持。

### Spring配置文件

Spring配置文件是个XML 文件，这个文件包含了类信息，描述了如何配置它们，以及如何相互调用。

### 什么是Spring IOC 容器？

Spring IOC 负责创建对象，管理对象（通过依赖注入（DI），装配对象，配置对象，并且管理这些对象的整个生命周期。

### IOC的优点是什么？

IOC 或 依赖注入把应用的代码量降到最低。它使应用容易测试，单元测试不再需要单例和JNDI查找机制。最小的代价和最小的侵入性使松散耦合得以实现。IOC容器支持加载服务时的饿汉式初始化和懒加载。

### ApplicationContext通常的实现是什么?

* FileSystemXmlApplicationContext ：此容器从一个XML文件中加载beans的定义，XML Bean 配置文件的全路径名必须提供给它的构造函数。
* ClassPathXmlApplicationContext：此容器也从一个XML文件中加载beans的定义，这里，你需要正确设置classpath因为这个容器将在classpath里找bean配置。
* WebXmlApplicationContext：此容器加载一个XML文件，此文件定义了一个WEB应用的所有bean

### Bean 工厂和 Application contets 有什么区别？

Application contexts提供一种方法处理文本消息，一个通常的做法是加载文件资源（比如镜像），它们可以向注册为监听器的 bean发布事件。另外，在容器或容器内的对象上执行的那些不得不由bean工厂以程序化方式处理的操作，可以在 Application contexts中以声明的方式处理。Application contexts实现了MessageSource接口，该接口 的实现以可插拔的方式提供获取本地化消息的方法。

### 一个Spring的应用看起来象什么？

* 一个定义了一些功能的接口。
* 这实现包括属性，它的Setter ， getter 方法和函数等。
* Spring AOP。
* Spring 的XML 配置文件。
* 使用以上功能的客户端程序。

### 什么是Spring beans?

Spring beans 是那些形成Spring应用的主干的java对象。它们被Spring IOC容器初始化，装配，和管理。这些beans通过容器中配置的元数据创建。比如，以XML文件中<bean/> 的形式定义。

Spring 框架定义的beans都是单件beans。在bean tag中有个属性”singleton”，如果它被赋为 TRUE，bean 就是单件，否则就是一个 prototype bean。默认是TRUE，所以所有在Spring框架中的beans 缺省都是单 件。

### 如何给Spring 容器提供配置元数据?

这里有三种重要的方法给Spring 容器提供配置元数据。

XML配置文件。

基于注解的配置。

基于java的配置。

### 一个 Spring Bean 定义 包含什么？

一个Spring Bean 的定义包含容器必知的所有配置元数据，包括如何创建一个bean，它的生命周期详情及它的依赖。

### 在 Spring中如何注入一个java集合？

Spring提供以下几种集合的配置元素：

* **list**类型用于注入一列值，允许有相同的值。
* **set** 类型用于注入一组值，不允许有相同的值。
* **map** 类型用于注入一组键值对，键和值都可以为任意类型。
* **props**类型用于注入一组键值对，键和值都只能为String类型

### @Required 注解

这个注解表明bean的属性必须在配置的时候设置，通过一个bean定义的显式的属性值或通过自动装配，若@Required注解的bean属性未被设置，容器将抛出BeanInitializationException。

### @Autowired 注

@Autowired 注解提供了更细粒度的控制，包括在何处以及如何完成自动装配。它的用法和@Required一样，修饰setter方法、构造器、属性或者具有任意名称和/或多个参数的PN方法。

### @Qualifier 注解

当有多个相同类型的bean却只有一个需要自动装配时，将@Qualifier 注解和@Autowire 注解结合使用以消除这种混淆，指定需要装配的确切的bean。

### JdbcTemplate

JdbcTemplate 类提供了很多便利的方法解决诸如把数据库数据转变成基本数据类型或对象，执行写好的或可调用的数据库操作语句，提供自定义的数据错误处理。



## SpringMVC面试题

### Springmvc的优点:

* 可以支持各种视图技术,而不仅仅局限于JSP；

* 与Spring框架集成（如IoC容器、AOP等）；

* 清晰的角色分配：前端控制器(dispatcherServlet) , 请求到处理器映射（handlerMapping), 处理器适配器（HandlerAdapter), 视图解析器（ViewResolver）。

* 支持各种请求资源的映射策略。

### Spring MVC的主要组件？

* 前端控制器 DispatcherServlet（不需要程序员开发）

作用：接收请求、响应结果，相当于转发器，有了DispatcherServlet 就减少了其它组件之间的耦合度。

* 处理器映射器HandlerMapping（不需要程序员开发）

* 根据请求的URL来查找Handler

* 处理器适配器HandlerAdapter

注意：在编写Handler的时候要按照HandlerAdapter要求的规则去编写，这样适配器HandlerAdapter才可以正确的去执行Handler。

* 处理器Handler（需要程序员开发）

* 视图解析器 ViewResolver（不需要程序员开发）

作用：进行视图的解析，根据视图逻辑名解析成真正的视图（view）

* 视图View（需要程序员开发jsp）

View是一个接口， 它的实现类支持不同的视图类型（jsp，freemarker，pdf等等）

### springMvc 的控制器是不是单例模式，如果是，有什么问题，怎么解决？

* 问题：单例模式，在多线程访问时有线程安全问题
* 解决方法：不要用同步，在控制器里面不能写字段

### SpringMvc 中控制器的注解

 @Controller：该注解表明该类扮演控制器的角色 

### @RequestMapping 注解用在类上的作用？

 作用：用来映射一个URL到一个类或者一个特定的处理方法上 

### 前台多个参数，这些参数都是一个对象，快速得到对象？

 方法：直接在方法中声明这个对象，SpringMvc就自动把属性赋值到这个对象里面 

### SpringMvc中函数的返回值？

String，ModelAndView，List，Set 等

一般String，Ajax请求，返回一个List集合

### SpringMvc中的转发和重定向?

* 转发：return：“hello”
* 重定向 ：return：“redirect:hello.jsp”

### SpringMvc和Ajax之间的相互调用？

 通过JackSon框架把java里面对象直接转换成js可识别的json对象，具体步骤如下： 

* 加入JackSon.jar
* 在配置文件中配置json的映射
* 在接受Ajax方法里面直接返回Object，list等，方法前面需要加上注解@ResponseBody

### Struts2 和 SpringMvc的区别

##### 入口不同：

* Struts2：filter过滤器
* SpringMvc：一个Servlet即前端控制器

##### 开发方式不同：

* Struts2：基于类开发，传递参数通过类的属性，只能设置为多例
* SpringMvc：基于方法开发(一个url对应一个方法)，请求参数传递到方法形参，可以为单例也可以为多例(建议单例)

##### 请求方式不同：

* Struts2：值栈村塾请求和响应的数据，通过OGNL存取数据
* SpringMvc：通过参数解析器将request请求内容解析，给方法形参赋值，将数据和视图封装成ModelAndView对象，最后又将ModelAndView中的模型数据通过request域传输到页面，jsp视图解析器默认使用的是jstl。

### DispatcherServlet

Spring的MVC框架是围绕DispatcherServlet来设计的，它用来处理所有的HTTP请求和响应。

### WebApplicationContext

WebApplicationContext 继承了ApplicationContext 并增加了一些WEB应用必备的特有功能，它不同于一般的ApplicationContext ，因为它能处理主题，并找到被关联的servlet。

### 什么是Spring MVC框架的控制器？

控制器提供一个访问应用程序的行为，此行为通常通过服务接口实现。控制器解析用户输入并将其转换为一个由视图呈现给用户的模型。Spring用一个非常抽象的方式实现了一个控制层，允许用户创建多种用途的控制器。

### @Controller 注解

该注解表明该类扮演控制器的角色，Spring不需要你继承任何其他控制器基类或引用Servlet API。

### @RequestMapping 注解

该注解是用来映射一个URL到一个类或一个特定的方处理法上。

###  **如何解决POST请求中文乱码问题，GET的又如何处理呢？** 

* 解决post请求乱码问题：

在web.xml中配置一个CharacterEncodingFilter过滤器，设置成utf-8；

~~~xml
<filter>

    <filter-name>CharacterEncodingFilter</filter-name>

    <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>

    <init-param>

        <param-name>encoding</param-name>

        <param-value>utf-8</param-value>

    </init-param>

</filter>

<filter-mapping>

    <filter-name>CharacterEncodingFilter</filter-name>

    <url-pattern>/*</url-pattern>

</filter-mapping>
~~~

*  get请求中文参数出现乱码解决方法有两个： 

1丶修改tomcat配置文件添加编码与工程编码一致，如下： 

~~~xml
<ConnectorURIEncoding="utf-8" connectionTimeout="20000" port="8080"protocol="HTTP/1.1" redirectPort="8443"/>
~~~

二丶另外一种方法对参数进行重新编码：

String userName = new String(request.getParamter("userName").getBytes("ISO8859-1"),"utf-8")

ISO8859-1是tomcat默认编码，需要将tomcat编码后的内容按utf-8编码。

### Spring MVC的异常处理 ？

答：可以将异常抛给Spring框架，由Spring框架来处理；我们只需要配置简单的异常处理器，在异常处理器中添视图页面即可。

###  怎样在方法里面得到Request,或者Session

 直接在方法的形参中声明request,SpringMvc就自动把request对象传入。 

###  如果想在拦截的方法里面得到从前台传入的参数,怎么得到？

 直接在形参里面声明这个参数就可以,但必须名字和传过来的参数一样 

### 怎么样把ModelMap里面的数据放入Session里面？

答：可以在类上面加上@SessionAttributes注解,里面包含的字符串就是要放入session里面的key。

###  SpringMvc里面拦截器是怎么写的：

 有两种写法,一种是实现HandlerInterceptor接口，另外一种是继承适配器类，接着在接口方法当中，实现处理逻辑；然后在SpringMvc的配置文件中配置拦截器即可： 

~~~xml
  <!-- 配置SpringMvc的拦截器 -->
 
<mvc:interceptors>
 
    <!-- 配置一个拦截器的Bean就可以了 默认是对所有请求都拦截 -->
 
    <bean id="myInterceptor" class="com.zwp.action.MyHandlerInterceptor"></bean>
 
    <!-- 只针对部分请求拦截 -->
 
    <mvc:interceptor>
 
       <mvc:mapping path="/modelMap.do" />
 
       <bean class="com.zwp.action.MyHandlerInterceptorAdapter" />
 
    </mvc:interceptor>
 
</mvc:interceptors>
~~~

### 注解原理：

注解本质是一个继承了Annotation的特殊接口，其具体实现类是Java运行时生成的动态代理类。我们通过反射获取注解时，返回的是Java运行时生成的动态代理对象。通过代理对象调用自定义注解的方法，会最终调用AnnotationInvocationHandler的invoke方法。该方法会从memberValues这个Map中索引出对应的值。而memberValues的来源是Java常量池。



## Mybatis面试题

### Ibatis和Mybatis？

* Ibatis：2010年，apache的Ibatis框架停止更新，并移交给了google团队，同时更名为MyBatis。从2010年后Ibatis在没更新过，彻底变成了一个孤儿框架。一个没人维护的框架注定被mybatis拍在沙滩上。
* Mybatis：Ibatis的升级版本。

### 什么是Mybatis的接口绑定，有什么好处？

Mybatis实现了DAO接口与xml映射文件的绑定，自动为我们生成接口的具体实现，使用起来变得更加省事和方便

### 什么情况用注解，什么情况用xml绑定？

* 注解使用情况：Sql语句简单时
* xml绑定使用情况：xml绑定 (@RequestMap用来绑定xml文件)

### Mybatis在核心处理类叫什么?

SqlSession

### 查询表名和返回实体Bean对象不一致，如何处理？

映射键值对即可

* column：数据库中表的列名
* property：实体Bean中的属性名

### Mybatis的好处？

* 把Sql语句从Java中独立出来。
* 封装了底层的JDBC，API的调用，并且能够将结果集自动转换成JavaBean对象，简化了Java数据库编程的重复工作。
* 自己编写Sql语句，更加的灵活。
* 入参无需用对象封装（或者map封装）,使用@Param注解

### Mybatis配置一对多？

* property：属性名
* column：共同列
* ofType：集合中元素的类型
* select：要连接的查询

### Mybatis配置一对一？

* property：属性名
* select：要连接的查询
* column：共同列
* javaType：集合中元素的类型

### ${} 和 #{}的区别？

* ${}：简单字符串替换，把${}直接替换成变量的值，不做任何转换，这种是取值以后再去编译SQL语句。
* \#{}：预编译处理，sql中的#{}替换成？，补全预编译语句，有效的防止Sql语句注入，这种取值是编译好SQL语句再取值。

>  总结：一般用#{}来进行列的代替

### Mybatis如何分页，分页原理？

* RowBounds对象分页
* 在Sql内直接书写，带有物理分页



> 文中部分面试题参考地址如下,点击文字即可跳转阅读:
>
> [SpringMVC常见面试题总结（超详细回答）]( https://blog.csdn.net/a745233700/article/details/80963758 )
>
> [史上最全69道Spring面试题和答案]( https://blog.csdn.net/zl1zl2zl3/article/details/81865407 )
>
> [Mybatis常见面试题总结]( https://blog.csdn.net/a745233700/article/details/80977133 )