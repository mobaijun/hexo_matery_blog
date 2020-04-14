---
title: java代码查错11道题
author: 墨白
top: false
cover: false
toc: true
mathjax: false
tags:
  - Java
categories:
  - Java
abbrlink: 2380575154
date: 2020-02-27 11:18:11
img:
coverImg:
password:
summary:
---



### 一

~~~java
abstract class Name {
    private String name;

    public abstract boolean isStupidName(String name) {
    }
}
~~~

 大侠们，这有何错误?
    答案: 错。abstract method必须以分号结尾，且不带花括号。 

### 二

~~~java
public class Something {
    void doSomething() {
        private String s = "";
        int l = s.length();
    }
}
~~~

 有错吗?
    答案: 错。局部变量前不能放置任何访问修饰符 (private，public，和protected)。final可以用来修饰局部变量
(final如同abstract和strictfp，都是非访问修饰符，strictfp只能修饰class和method而非variable)。 

### 三

~~~java
abstract class Something {
    private abstract String doSomething();
}
~~~

 这好像没什么错吧?
    答案: 错。abstract的methods不能以private修饰。abstract的methods就是让子类implement(实现)具体细节的，怎么可以用private把abstract
method封锁起来呢? (同理，abstract method前不能加final)。 

### 四

~~~java
public class Something {
    public int addOne(final int x) {
        return ++x;
    }
}
~~~

这个比较明显。
    答案: 错。int x被修饰成final，意味着x不能在addOne method中被修改。

### 五

~~~java
public class Something {
    public static void main(String[] args) {
        Other o = new Other();
        new Something().addOne(o);
    }

    public void addOne(final Other o) {
        o.i++;
    }
}

class Other {
    public int i;
}
~~~

 和上面的很相似，都是关于final的问题，这有错吗?
    答案: 正确。在addOne method中，参数o被修饰成final。如果在addOne method里我们修改了o的reference(比如: o = new Other();)，那么如同上例这题也是错的。但这里修改的是o的member vairable(成员变量)，而o的reference并没有改变。 

### 六

~~~java
class Something {
    int i;

    public void doSomething() {
        System.out.println("i = " + i);
    }
}
~~~

 有什么错呢? 看不出来啊。
    答案: 正确。输出的是"i = 0"。int i属於instant variable (实例变量，或叫成员变量)。instant variable有default value。int的default value是0。 

### 七

~~~java
class Something {
    final int i;

    public void doSomething() {
        System.out.println("i = " + i);
    }
}
~~~

和上面一题只有一个地方不同，就是多了一个final。这难道就错了吗?
    答案: 错。final int i是个final的instant variable (实例变量，或叫成员变量)。final的instant variable没有default value，必须在constructor (构造器)结束之前被赋予一个明确的值。可以修改为"final int i = 0;"。

### 八

~~~java
public class Something {
    public static void main(String[] args) {
        Something s = new Something();
        System.out.println("s.doSomething() returns " + doSomething());
    }

    public String doSomething() {
        return "Do something ...";
    }
}
~~~

 看上去很完美。
    答案: 错。看上去在main里call doSomething没有什么问题，毕竟两个methods都在同一个class里。但仔细看，main是static的。static method不能直接call non-static methods。可改成"System.out.println("s.doSomething() returns " + s.doSomething());"。同理，static method不能访问non-static instant variable。 

### 九

 此处，Something类的文件名叫OtherThing.java 

~~~java
class Something {
    private static void main(String[] something_to_do) {
        System.out.println("Do something ...");
    }
}
~~~

 这个好像很明显。
    答案: 正确。从来没有人说过Java的Class名字必须和其文件名相同。但public class的名字必须和文件名相同。 

### 十

~~~java
interface A {
    int x = 0;
}

class B {
    int x = 1;
}

class C extends B implements A {
    public void pX() {
        System.out.println(x);
    }

    public static void main(String[] args) {
        new C().pX();
    }
}
~~~

 答案：错误。在编译时会发生错误(错误描述不同的JVM有不同的信息，意思就是未明确的x调用，两个x都匹配（就象在同时import java.util和java.sql两个包时直接声明Date一样）。对于父类的变量,可以用super.x来明确，而接口的属性默认隐含为 public static final.所以可以通过A.x来明确。 

### 十一

~~~java
interface Playable {
    void play();
}

interface Bounceable {
    void play();
}

interface Rollable extends Playable, Bounceable {
    Ball ball = new Ball("PingPang");
}

class Ball implements Rollable {
    private String name;

    public String getName() {
        return name;
    }

    public Ball(String name) {
        this.name = name;
    }

    public void play() {
        ball = new Ball("Football");
        System.out.println(ball.getName());
    }
}
~~~

这个错误不容易发现。

答案: 错。"interface Rollable extends Playable, Bounceable"没有问题。interface可继承多个interfaces，所以这里没错。问题出在interface Rollable里的"Ball ball = new Ball("PingPang");"。任何在interface里声明的interface variable (接口变量，也可称成员变量)，默认为public static final。也就是说"Ball ball = new Ball("PingPang");"实际上是"public static final Ball ball = new Ball("PingPang");"。在Ball类的Play()方法中，"ball = new Ball("Football");"改变了ball的reference，而这里的ball来自Rollable interface，Rollable interface里的ball是public static final的，final的object是不能被改变reference的。因此编译器将在"ball = new Ball("Football");"