---
layout: post
title:  "面试常见问题"
date:   2020-11-09
categories: work
---

### 1  写出int 、bool、 float 、指针变量与 “零值”比较的if 语句

```c++
//int与零值比较 
if ( n == 0 )
if ( n != 0 )
 
//bool与零值比较 
if   (flag) //   表示flag为真 
if   (!flag) //   表示flag为假 
 
//float与零值比较 
const float EPSINON = 0.00001;
if ((x >= - EPSINON) && (x <= EPSINON) //其中EPSINON是允许的误差（即精度）。
//指针变量与零值比较 
if (p == NULL)
if (p != NULL)
```

### 2 Ｃ 语言的 malloc 和 Ｃ＋＋ 中的 new 有什么区别

- new 、delete 是操作符，可以重载，只能在C++ 中使用。  
- malloc、free 是函数，可以覆盖，C、C++ 中都可以使用。  
- new 可以调用对象的构造函数，对应的delete 调用相应的析构函数。  
- malloc 仅仅分配内存，free 仅仅回收内存，并不执行构造和析构函数  
- new 、delete 返回的是某种数据类型指针，malloc、free 返回的是void 指针。  
注意：malloc 申请的内存空间要用free 释放，而new 申请的内存空间要用delete 释放，不要混用。  


### 3  简述C、C++程序编译的内存分配情况

- 从静态存储区域分配

内存在程序编译时就已经分配好，这块内存在程序的整个运行期间都存在。速度快、不容易出错， 因为有系统会善后。例如全局变量，static 变量，常量字符串等。

- 在栈上分配

执行函数时，函数内局部变量的存储单元都在栈上创建，函数执行结束时这些存储单元自动被释 放。栈内存分配运算内置于处理器的指令集中，效率很高，但是分配的内存容量有限。大小为2M。

- 从堆上分配

即动态内存分配。程序在运行的时候用 malloc 或new 申请任意大小的内存，程序员自己负责在何 时用free 或delete 释放内存。动态内存的生存期由程序员决定，使用非常灵活。如果在堆上分配了空间，就有责任回收它，否则运行的程序会出现内存泄漏，另外频繁地分配和释放不同大小的堆空间将会产生 堆内碎块。


### 4  对c++中的smart pointer四个智能指针：shared_ptr,unique_ptr,weak_ptr,auto_ptr的理解

- unique_ptr

unique_ptr实现独占式拥有或严格拥有概念，保证同一时间内只有一个智能指针可以指向该对象。它对于避免资源泄露(例如“以new创建对象后因为发生异常而忘记调用delete”)特别有用。

- shared_ptr

shared_ptr实现共享式拥有概念。多个智能指针可以指向相同对象，该对象和其相关资源会在“最后一个引用被销毁”时候释放。从名字share就可以看出了资源可以被多个指针共享，它使用计数机制来表明资源被几个指针共享。可以通过成员函数use_count()来查看资源的所有者个数。除了可以通过new来构造，还可以通过传入auto_ptr, unique_ptr,weak_ptr来构造。当我们调用release()时，当前指针会释放资源所有权，计数减一。当计数等于0时，资源会被释放。

成员函数：

use_count 返回引用计数的个数  
unique 返回是否是独占所有权( use_count 为 1)  
swap 交换两个 shared_ptr 对象(即交换所拥有的对象)  
reset 放弃内部对象的所有权或拥有对象的变更, 会引起原有对象的引用计数的减少  
get 返回内部对象(指针), 由于已经重载了()方法, 因此和直接使用对象是一样的.如 shared_ptrsp(new int(1)); sp 与 sp.get()是等价的  

### 5   webrtc p2p连接过程

![img](/assets/webrtc_connection.png)

### 6   STUN与TURN的区别

STUN ( Simple Traversal of UDP Through NATs ) 使用`UDP`进行`NATs`穿透。  

TRUN ( Traversal Using Relays around NAT:Relay Extensions to Session Traversal Utilities for NAT ) 则是`STUN`的增强版，在无法使用`STUN`进行穿透时，通过中继的方式实现`P2P`互通。