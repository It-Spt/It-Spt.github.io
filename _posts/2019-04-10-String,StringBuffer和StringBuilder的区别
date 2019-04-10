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

  我们在做Java开发中String的使用是非常平凡的，面试时也常常会被问到，那么为什么有了String还会有StringBuffer和StringBuilder呢？
一个东西他可以存在那么必然有它的意义，这篇文章就会讲述他们的不同。


### 1.了解String、StringBuffer和StringBuilder

{% highlight ruby %}
1.public final class String implements Serializable, Comparable<String>, CharSequence 
2.public final class StringBuilder extends AbstractStringBuilder implements Serializable, CharSequence
3.public final class StringBuffer extends AbstractStringBuilder implements Serializable, CharSequence
{% endhighlight %}

  通过上面的源码我们可以看到，他们都是final修饰的，成员方法也都是final修饰符修饰的，使用final修饰的类是不可以被继承，
方法是不可以重写或重载的。在早期的JVM实现版本中，被final修饰的方法会被转为内嵌调用以提升执行效率。而从Java SE5/6开始，
就渐渐摈弃这种方式了。因此在现在的Java SE版本中，不需要考虑用final去提升方法调用效率。只有在确定不想让该方法被覆盖时，
才将方法设置为final。


### 2.String、StringBuffer和StringBuilder的不同
