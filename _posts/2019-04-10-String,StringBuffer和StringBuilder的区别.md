---
layout: post
title:  "String、StringBuffer和StringBuilder的区别"
categories: 编程语言
tags:  Java String  
author: super-pt
---

* content
{:toc}
## 前言

  我们在做Java开发中String的使用是非常频繁的，面试时也常常会被问到，那么为什么有了String还会有StringBuffer和StringBuilder呢？
一个东西他可以存在那么必然有它的意义，这篇文章就会讲述他们的不同。





## 一.了解String、StringBuffer和StringBuilder

{% highlight ruby %}
1.public final class String implements Serializable, Comparable<String>, CharSequence 
2.public final class StringBuilder extends AbstractStringBuilder implements Serializable, CharSequence
3.public final class StringBuffer extends AbstractStringBuilder implements Serializable, CharSequence
{% endhighlight %}

  通过上面的源码我们可以看到，他们都是final修饰的，成员方法也都是final修饰符修饰的，使用final修饰的类是不可以被继承，
方法是不可以重写或重载的。在早期的JVM实现版本中，被final修饰的方法会被转为内嵌调用以提升执行效率。而从Java SE5/6开始，
就渐渐摈弃这种方式了。因此在现在的Java SE版本中，不需要考虑用final去提升方法调用效率。只有在确定不想让该方法被覆盖时，
才将方法设置为final。


## 二.String、StringBuffer和StringBuilder的不同
  这三个最主要的不同有两点，```运行速度```和```线程安全```。
### 1.运行速度
  ```String```<```StringBuilder```<```StringBuffer```
  ``String慢的原因``
  因为String是字符串常量，而后两者是字符串变量。我们看看源码：
  {% highlight ruby %}
  private final char[] value;
  {% endhighlight %}
  这是String的源码中的成员，我们可以看到他的value是final修饰的，上面有说说final修饰的是不可变的。
   {% highlight ruby %}
  String a = "123";
  System.out.print(a);
  a= "456";
  System.out.print(a);
  {% endhighlight %}
  上面这段代码打印的第一个结果是123，第二个是456，这个大家肯定都知道。可是string不是不可变的吗？为什么改变了？
  ```原因```
  上面的a只是一个字符串对象的引用，"123"/"456"并没有存到a中，a中保存的只是一个地址，指向的是真正的对象，所以"123"还是没有改变的。
 {% highlight ruby %}
  String a = "123";
  String b = "456";
  String b += a;
  System.out.print(b);
  {% endhighlight %}
   上面这段代码打印的第一个结果是123456,那String是怎么完成的拼接的呢？
   实际上最后编译后使用的是StringBuffer 的append方法新建了一个字符串对象。
   以上就是为什么字符串是最慢的原因了，我们再来看看另外两个。
   ``StringBuffer vs StringBuilder``
