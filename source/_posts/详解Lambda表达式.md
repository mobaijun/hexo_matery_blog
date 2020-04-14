---
title: 详解Lambda表达式
author: 框架师|墨白
img: 
coverImg: 
top: false
abbrlink: 4260202441
cover: true
toc: true
mathjax: false
summary: 
tags:
  - Lambda
categories:
  - Java
date: 2019-12-06 19:41:03
password:
---

##### 引言:

函数式编程思想概述:在数学中，函数就是有输入量、输出量的一套计算方案，也就是“拿什么东西做什么事情”。相对而言，面向对象过分强调“必须通过对象的形式来做事情”，而函数式思想则尽量忽略面向对象的复杂语法——强调做什么，而不是以什么形式做。做什么，而不是怎么做,我们真的希望创建一个匿名内部类对象吗？不。我们只是为了做这件事情而不得不创建一个对象。



我们真正希望做的事情是：将 run 方法体内的代码传递给 Thread 类知晓。

传递一段代码——这才是我们真正的目的。而创建对象只是受限于面向对象语法而不得不采取的一种手段方式。那，有没有更加简单的办法？如果我们将关注点从“怎么做”回归到“做什么”的本质上，就会发现只要能够更好地达到目的，过程与形式其实并不重要。



* ##### 了解Lambda的优化

当需要启动一个线程去完成任务时，通常会通过 java.lang.Runnable 接口来定义任务内容，并使用 java.lang.Thread 类来启动该线程。

传统写法,代码如下：

~~~java
/**
 * @Author：Auser·杰
 * @DATE：2019/11/4 21:46
 */
 public class Demo {
   public static void main(String[] args) {
     new Thread(new Runnable() {
       @Override
       public void run() {
        System.out.println("多线程任务执行！");
      }
  }).start();
 }
}
~~~

本着“一切皆对象”的思想，这种做法是无可厚非的：首先创建一个 Runnable 接口的匿名内部类对象来指定任务内容，再将其交给一个线程来启动。



代码分析:

1. 对于 Runnable 的匿名内部类用法，可以分析出几点内容：
2. Thread 类需要 Runnable 接口作为参数，其中的抽象 run 方法是用来指定线程任务内容的核心；
3. 为了指定 run 的方法体，不得不需要 Runnable 接口的实现类；
4. 为了省去定义一个 RunnableImpl 实现类的麻烦，不得不使用匿名内部类；
5. 必须覆盖重写抽象 run 方法，所以方法名称、方法参数、方法返回值不得不再写一遍，且不能写错；
6. 而实际上，似乎只有方法体才是关键所在。

* ##### Lambda表达式写法,

代码如下：

借助Java 8的全新语法，上述 Runnable 接口的匿名内部类写法可以通过更简单的Lambda表达式达到等效：

~~~java
/**
 * @Author：Auser·杰
 * @DATE：2019/11/4 21:50
 */
public class Demo02LambdaRunnable {
  public static void main(String[] args) {         // 启动线程
    new Thread(() -> System.out.println("多线程任务执行！")).start(); 
  }
}
~~~

这段代码和刚才的执行效果是完全一样的，可以在1.8或更高的编译级别下通过。从代码的语义中可以看出：我们启动了一个线程，而线程任务的内容以一种更加简洁的形式被指定。不再有“不得不创建接口对象”的束缚，不再有“抽象方法覆盖重写”的负担，就是这么简单！



* ##### Lambda的格式

标准格式:

Lambda省去面向对象的条条框框，格式由3个部分组成：

1. 一些参数
2. 一个箭头
3. 一段代码

Lambda表达式的标准格式为：

~~~java
1(参数类型 参数名称) -> { 代码语句 }
~~~

格式说明：

* 小括号内的语法与传统方法参数列表一致：无参数则留空；多个参数则用逗号分隔。
* -> 是新引入的语法格式，代表指向动作。
* 大括号内的语法与传统方法体要求基本一致。

匿名内部类与lambda对比:

~~~java
 /**
  * @Author：Auser·杰
  * @DATE：2019/11/4 21:58
  */
 new Thread(new Runnable() {
 @Override
 public void run() {
     System.out.println("多线程任务执行！");
     }
    }).start()
~~~

仔细分析该代码中， Runnable 接口只有一个 run 方法的定义：

* public abstract void run();即制定了一种做事情的方案（其实就是一个方法）：

1. 无参数：不需要任何条件即可执行该方案。
2. 无返回值：该方案不产生任何结果。
3. 代码块（方法体）：该方案的具体执行步骤。

* 同样的语义体现在 Lambda 语法中，要更加简单：

```
1() -> System.out.println("多线程任务执行！")
```

1. 前面的一对小括号即 run 方法的参数（无），代表不需要任何条件；
2. 中间的一个箭头代表将前面的参数传递给后面的代码；
3. 后面的输出语句即业务逻辑代码。

* #####  Lambda 参数和返回

下面举例演示 java.util.Comparator接口的使用场景代码，其中的抽象方法定义为：

* public abstract int compare(T o1, T o2);

当需要对一个对象数组进行排序时， Arrays.sort 方法需要一个 Comparator 接口实例来指定排序的规则。假设有一个 Person 类，含有 String name 和 int age 两个成员变量：

~~~java
public class Person {
    private String name;
    private int age;

   // 省略构造器、toString方法与Getter Setter
}
~~~

传统写法如果使用传统的代码对 Person[] 数组进行排序，写法如下：

```java
/**
 * @Author：Auser·杰
 * @DATE：2019/11/4 22:35
 */
public class TestComparator {
    public static void main(String[] args) {
        // 本来年龄乱序的对象数组
        Person[] array = {new Person("墨白", 19),
                new Person("小柠檬不酸", 18),
                new Person("大白", 20)};
        // 匿名内部类
        Comparator<Person> comp = new Comparator<Person>() {
            @Override
            public int compare(Person o1, Person o2) {
                return o1.getAge() - o2.getAge();
            }
        };
        Arrays.sort(array, comp);
        // 第二个参数为排序规则，即Comparator接口实例
        for (Person person : array) {
            System.out.println(person);
        }
    }
 }
```

这种做法在面向对象的思想中，似乎也是“理所当然”的。其中 Comparator 接口的实例（使用了匿名内部类）代表了“按照年龄从小到大”的排序规则。

代码分析:

下面我们来搞清楚上述代码真正要做什么事情。

1. 为了排序， Arrays.sort 方法需要排序规则，即 Comparator 接口的实例，抽象方法compare 是关键；
2. 为了指定 compare 的方法体，不得不需要 Comparator 接口的实现类；
3. 为了省去定义一个 ComparatorImpl 实现类的麻烦，不得不使用匿名内部类；
4. 必须覆盖重写抽象 compare 方法，所以方法名称、方法参数、方法返回值不得不再写一遍，且不能写错；
5. 实际上，只有参数和方法体才是关键。

##### Lambda写法

~~~java
/**
 * 2  * @Author：Auser·杰
 * 3  * @DATE：2019/11/4 21:50
 * 4
 */
public class TestComparatorLambda {
    public static void main(String[] args) {
        Person[] array = {new Person("墨白", 19),
                new Person("小柠檬不酸", 18),
                new Person("大白", 20)};
        Arrays.sort(array, (Person a, Person b) -> {
            return a.getAge() - b.getAge();
        });
        for (Person person : array) {
            System.out.println(person);
        }
    }
}
~~~

省略规则

在Lambda标准格式的基础上，使用省略写法的规则为：

1. 小括号内参数的类型可以省略；

2. 如果小括号内有且仅有一个参，则小括号可以省略；

3. 如果大括号内有且仅有一个语句，则无论是否有返回值，都可以省略大括号,return关键字及语句分号。

> 备注：掌握这些省略规则后，请对应地回顾本文开头的多线程案例



* ##### 可推导即可省略

Lambda强调的是“做什么”而不是“怎么做”，所以凡是可以根据上下文推导得知的信息，都可以省略。例如上例还可以使用Lambda的省略写法：

~~~java
Runnable接口简化:
1. () -> System.out.println("多线程任务执行！")
Comparator接口简化:
2. Arrays.sort(array, (a, b) -> a.getAge() - b.getAge());
~~~

* Lambda的前提

Lambda的语法非常简洁，完全没有面向对象复杂的束缚。但是使用时有几个问题需要特别注意：

1. 使用Lambda必须具有接口，且要求接口中有且仅有一个抽象方法。 无论是JDK内置的Runnable 、 Comparator 接口还是自定义的接口，只有当接口中的抽象方法存在且唯一时，才可以使用Lambda。
2. 使用Lambda必须具有上下文推断。 也就是方法的参数或局部变量类型必须为Lambda对应的接口类型，才能使用Lambda作为该接口的实例。

> 备注：有且仅有一个抽象方法的接口，称为“函数式接口”。

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

