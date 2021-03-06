---
layout:     post
title:      进程（procress）和线程（Thread）的简单解释
subtitle:   
date:       2019-05-14
author:     DoubleWay
header-img: img/post-bg-coffee.jpeg
catalog: 	 true
tags:
    - java
    - 进程
---
进程（procress）和线程（Thread）是操作系统的基本概念，看到一篇[文章](https://www.cnblogs.com/dreamroute/p/5207813.html)比较具体的描述了进程与线程的关系,
计算机的核心是CPU，它承担了计算机的所有计算工作，就像一座工厂，在时刻运行。  
进程就像工厂里一个个车间工作室，假如工厂的电力是有限的，一次只能提供一个车间工作，这个车间在工作时，其他的车间必须等待，进程就像工厂的车间，CPU就是工厂，单个cpu每次只能进行一个任务，只能有一个进程处于运行状态，其他进程处于非运行状态。
在每一个车间中，会有许多工人一起协同工作，而线程（Thread）就相当于这些工人，一个进程包含多个线程。  
在车间中分为许多个房间，这些房间所有的工人都可以进入，代表进程的内存空间是共享的，进程里的所有线程都可以使用进程的共享内存。  
但是，车间里的房间也是分大小的，有些房间大，有些房间小，比如厕所，一次只能一个人使用，其他人要想使用，就必须排队，就像进程中某块共享内存区域，一次只能一个线程使用，其他线程要想使用，就必须排队，等这个线程结束后才能使用。  
怎样防止在使用的时候别人进行呢，就像上厕所的时候，进去后就会上锁，等使用完以后才会打开锁出来，进程也是一样的，上的这个锁就是[“互斥锁”](https://baike.baidu.com/item/%E4%BA%92%E6%96%A5%E9%94%81/841823?fr=aladdin)，防止多个进程线程同时读写一块内存区域。  
还有些“房间”比较大，一次能容纳n个人，就像有些内存区域能供n个线程同时使用，如果数量大于n就只能在外面排队，等待有空的位置出来。这时怎么防止别人进入呢，最好的方法就是提供n把钥匙，一个人进入就拿一把钥匙，出来的时候再放回原地，别人看到而没有钥匙了就只能在外面等待，这n把钥匙，就是[“信号量”](https://baike.baidu.com/item/%E4%BF%A1%E5%8F%B7%E9%87%8F/9807501?fr=aladdin),用信号量-->钥匙,来保证多线程时不会冲突。  
对比两种情况可以看出，前者是后者的极端，只有一把钥匙的情况下。  
