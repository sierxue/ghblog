+++
author = "飞狐"
categories = ["Java","Java Concurrency","翻译"]
date = "2017-04-01T21:57:30+08:00"
description = "Blog of Rosen Lu"
keywords = ["java concurrency"]
title = "3. [译]多线程的成本"

+++
本文翻译自**[Java Concurrency / Multithreading Costs](http://tutorials.jenkov.com/java-concurrency/costs.html)**

从一个单线程程序切换为多线程程序在给我们带来好处的同时也会产生一些额外的成本，不要因为会使用多线程就将一个程序变为多线程实现。在准备使用多线程时，我们应该有一个清楚的认识：使用多线程带来的好处大于其成本，当有不确定时，我们应该尝试度量应用程序的性能和响应性来决定是否采用多线程，而不是靠猜来决定。

<!--more-->

## 更复杂的设计
尽管多线程应用程序的某些部分比单线程应用程序更简单，但其它部分却更为复杂。在执行通过多线程访问共享数据时需要特别注意，同时多线程间的交互也不是那么简单,由不正确的线程同步引起的错误可能会非常难以检测、复现和修复。

## 上下文切换开销
当CPU从执行一个线程切换到执行另外一个线程时，CPU需要保存当前线程的本地数据，程序指针等，并加载下一个线程的本地数据，程序指针等来执行线程，这种切换被称作上下文切换，CPU从一个线程的上下文中执行切换到在另一个线程的上下文中执行。

上下文切换的代价并不便宜，在线程间要避免不必要的切换。可以在维基百科上阅读 **[Context switch](https://en.wikipedia.org/wiki/Context_switch)**来了解更多关于上下文切换的知识。

## 加重资源消耗
线程需要计算机的一些资源才能运行，除了CPU时间之外，线程需要一些内存来维护其本地堆栈，它也可能会占用操作系统的一些资源来管理该线程。我们可以尝试创建100个什么操作也没有的等待线程来看看在运行这些线程时应用程序需要多少内存。 

<–翻译结束!–>