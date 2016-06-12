---

layout: post
title: Docker回顾
category: 技术
tags: Docker
keywords: Docker

---

## 前言

对于一个比较熟悉的知识，回味回味，经常能整出点新的想法来。

## Docker VS vm

两者都算是一种虚拟化技术，那么一个虚拟机需要什么？内存，cpu，网卡等

docker和vm的最主要区别就是

1. vm是虚拟出这些设备。假设vm中的进程申请内存，是经过Guest OS，hypervisior，Host os最终得到分配。
2. docker是隔离出这些设备（当然，网卡啥的也是虚拟的）。container中的进程直接向Host Os申请即可。


## cgroup和namespace

介绍Docker的文章都会说：cgroup负责资源限制，namepace负责资源隔离。

我们知道，Host OS中的进程，申请内存往往是没有限制的，cgroup则提供了解决了这个问题。

对于隔离，什么叫隔离，隔离了什么呢？隔离就是不能相互访问，甚至感知不到彼此的存在。对于Host OS中的进程，OS保证不能访问彼此的地址空间（存储程序和程序），但更大的资源范围，比如内存、cpu、文件系统，则是共享的，有时也能感知到对方的存在，否则也没办法rpc。namespace能做到在更大的资源范围内隔离彼此。举个例子，不同namespace的进程可以具备相同的进程id。

## Docker的三大概念

镜像、容器和仓库。其实跟VirtualBox对比就是：box文件，vm运行实例和`http://www.vagrantbox.es/`。docker在这里的作用就类似于vagrant。

## 使用Docker要解决的几个基本问题

完全的隔离并不是好事，免不了要通信和共享

### Docker的网络模型

现实生活中，以太网的拓扑结构在不断的发展（简单以太网、vlan和vxlan等），那么如何在单机环境或多机环境中用虚拟网络模拟物理网络，是一个重要问题。换个描述方式：

1. 如何实现容器互通
2. 如何实现容器与宿主机互通
3. 如何实现容器与宿主机所在网络的其它物理主机互通
4. 如何实现跨主机容器互通

### Docker文件系统

类似的

1. 容器之间如何共享文件
2. 容器与宿主机之间如何共享文件
3. 跨主机容器之间如何共享文件

## Docker实践

为什么要用到docker，这就要谈到其优势，它的优势分为两部分

1. 虚拟化技术本身的优势

    资源可以更细粒度的分配和释放（以前只能是物理机维度，并且不能够软件定义）。或者说，先有“资源可以更细粒度的分配和释放”的需求，然后催生了虚拟化技术，然后出现了虚拟网络模拟现实网络之类的问题。

2. docker相对于其它虚拟化技术的优势（其实，OpenStack也可以做到以下几点，但OpenStack（作为IaaS）侧重点不在这里，一个Openstack VM通常也不会只跑一个应用）

    - 隔离性。一个应用程序的可靠运行，除了代码的正确性，一个可靠地env是必不可少的一部分，有了docker，这个env可以归这个应用程序专有。
    
    - 可移植性。env可以像配置文件一样保存和转移。
    
    - 进程级的虚拟化，非常有利于扩容和缩容时的响应速度。
