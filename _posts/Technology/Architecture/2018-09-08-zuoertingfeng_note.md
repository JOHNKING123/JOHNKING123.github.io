---

layout: post
title: 《左耳听风》笔记
category: 技术
tags: Architecture
keywords: 左耳听风

---

## 简介（持续更新）

真的建议大家没事购买一些课程，哪怕这些东西你已经全部知道，因为“横看成岭侧成峰”，切入点不同，感受不同，视角不同，一样的事情知道别人是怎么想的也很有意思。同时这些东西一般是成体系的，可以将自己零碎的知识串起来。

## 技术变现

主要两点：自己得行，怎么行？告诉别人自己行：

1. 坚持，建立正向循环
2. 关注有价值的东西，价值受供需影响，供小于求的东西就是有价值，供大于求的东西少做或让别人做。
3. 关注技术趋势，要看清技术趋势，你需要了解历史。就像一个球运动一样，你要知道这个球未来运动的地方，是需要观察球已经完成运动的轨迹才知道的。要看一个新的技术是否顺应发展趋势，你需要将一些老技术的本质吃的很透。
4. 动手能力很重要
5. 关注技术付费点：赚钱点；省钱点
6. 提升自己的能力和经历
7. 找到有价值的信息源，微博、知乎等有价值的信息不多，最好的方式是google 输入 xx Best practise
8. 输出观点和价值观、高质量的朋友圈

## 技术领导力

技术分为两种

1. 核心，比如引擎之于汽车，但很多人或者未发觉，或者发觉了做不了
2. 辅助/工程方面的技术，让汽车跑的更安全更有效率

总是在提供解决问题的思路和方案的人才是有技术领导力的人。那么如何做到呢？

1. 吃透基础技术。对基础技术的学习能让你更好的、更快的掌握高维度的技术。PS：正是因为一些积累，笔者现在可以一两天看完一本技术书，一天对一个较为复杂的框架的源码有所认识。
2. 提高学习能力。所谓学习能力，就是能够很快的学习新技术，又能在关键技术上深入的能力。
3. 坚持做正确的事儿，包括但不限于

	* 提高效率的事儿、自动化的事儿
	* 掌握前沿技术
	* 知识密集型的事儿

4. 高标准要求自己。PS：一些框架的源码比如docker、kubernetes 等，不是难，而你是自己都没有勇气看

技术的发展过程非常重要，从中可以看到非常具体的思潮和思路，这些东西比go和docker来说更有价值。让我重新思考已掌握的技术以及如何更好的解决已有的问题。

阅读文档：作者一般的做法是先通读一遍文档，了解文档中所涉及的技术，重点是了解这个技术所涉及的面和其解决问题的思路。知道整个技术的脉络，而不是死记硬背。

## 故障处理

出现故障时，最重要的不是debug 故障，而是尽可能减少故障的影响范围，并尽可能快地修复问题。平时要故障演练，比如随意关闭线上的几台机器。在故障排除后，如何做故障复盘以及整改优化则更为重要。

1. 优化故障获知和故障定位的时间，如何做到更短，有哪些地方可以自动化等
2. 优化故障的处理方式，故障处理时的信息是否全透明，人员安排是否得当等
3. 优化开发过程中的问题，架构设计、技术欠债、codereview等
4. 优化团队能力，包括且不限于技术能力、工程意识等

一个技术问题，后面隐藏的是工程能力问题，工程能力问题后面隐藏的是管理问题， 管理问题后面隐藏的是一个公司文化问题，公司文化问题则隐藏着创始人问题。你不可能在一个复杂环境下根本地解决问题。如果你想要从根本上改善一个事儿，那首先得把从各方面简化了。

不出故障或处理故障靠的是能力，惩罚机制能够加强coder少出故障的意愿，但coder 的意愿和能力 没有直接关系，因此惩罚直接责任人是不合适的。


## 表象和本质

在我们的生活和工作中，总是会有很多人混淆一些看似有联系，实则却关系不大的词和概念，分辨不清事物的表象和本质。比如加班和产出、努力和成功、速度和效率等

不知道对什么感兴趣，不知道自己擅长什么？

关于兴趣和投入：兴趣是需要保持的，不能持久的兴趣，意义不大；兴趣是可以培养出来的。所以，**一开始很有兴趣或毫无兴趣都是表象，它们后面都有一个比较本质的东西：那就是你在做这件事儿时的一种正反馈，其实就是成就感。**兴趣只是开始，而能让人不断投入时间和精力的则是正反馈， 是成就感。

学习一门语言或者一项技术 是否只有找到了相应的工作 才学得好？

工作能让我们带着问题和场景去解决问题，有同事和高手的帮助，在讨论中学习，可以更有效率的学习和成长。所以，**不是找到了相应的工作我们才可以学好一项技术，而是，我们在通过解决实际问题， 和他人讨论，获得高手帮助的环境下，能更快更有效率的学习和成长。** 如果这几个要素不成立，工作也帮不到你。找工作不只是找用这个技术的工作，更是找场景，找实际问题，找团队。 PS：从大牛的表述可以看到，作为一项自信逻辑能力的理工男，自己在思考这类问题时非常混乱，非常汗颜。

技术的价值？

1. 与蒸汽机同时代的其它技术，比如化学、冶金等技术含量更高，但为何是蒸汽机代表了第一次工业革命？
2. 为什么“电灯”的发明比电更令人印象深刻？
3. 在一个基础技术被广泛使用的过程中，如何规模化也是一个关键技术

趋势和未来

这个世界的技术趋势和未来其实是被人控制的，具体的说是被那些有权有势的公司或国家来控制的，至少短期的未来一定是他们控制的。也就是说，技术的未来要去哪，基本上就是这个世界上有钱有势的人把财富投到哪个领域，也就是大公司或大国们的规划。投钱 ==> 发展 ==> 经过发展后的领域成为未来（不投钱的领域没发展/发展不大，十年后和今年一样，怎么会是未来）。PS：有点像以前 还有星探，现在直接 生产明星。

## 分布式架构的冰与火

下图主要集中在分布式系统的 应用于运维 角度。如何学习分布式参见 [分布式系统小结](http://qiankunli.github.io/2018/04/16/distributed_system_review.html)

![](/public/upload/architecture/zuoerduohaozi_distribution_system.png)

一个分布式系统（相对单体系统）有哪些问题，在下篇讲下这些问题在工程实现上如何体现：

1. 分布式系统，soa 乃至微服务也是一个分布式系统
1. 分布式系统架构的难点在于：系统设计、管理和运维。PS：从这可以看出业务模型不是最难点，比如Storm的Topology、Spark的rdd，理念很厉害，但这些理念能够落地 是最为困难的，包括且不限于解决可用性、扩展性等问题 ==> 分布式系统的共性问题 ==> 也正是我们要学习的。
2. SOA 架构是构造分布式计算应用程序的方法，它采用标准的表示方式（就像spring 业务类一般有一个接口类一样），将应用程序功能作为服务提供给用户/其它服务。就像类与类之间会产生依赖一样，服务于服务之间 也会产生依赖。这一个依赖可以由调用方解决，也可以由中间件解决（类体现为ioc，soa 则体现为esb）。PS：道理果然是相通的
3. 微服务在测试、运维和服务管理等方面比较麻烦，需要一套比较好的PaaS 平台，包括两块

	* 类似Spring cloud 一样需要提供各种配置服务、服务发现、路由、控制总线等
	* 像k8s 一样提供各式各样的部署与调度方式

4. 服务、数据、流量调度。这三个方面一起说的时候，找一找感觉。

	* 分布式的服务调度需要一个分布式的存储系统来支持服务的数据调度。各大公司都在分布式的数据库上做各种各样的创新，他们都在使用底层的分布式文件系统来做存储引擎，把存储和计算分离开来，然后使用分布式一致性的数据同步协议的算法来为上层提供高可用、高扩展的支持。
	* 服务调度有几个理解：和流量调度将流量动态调整到各个节点；服务的扩容缩容；应用集群与数据集群的扩大与压缩；伙伴服务编排（编排这词儿在k8s和在微服务里可能不是一个意思）
5. 分布式系统 几乎没有一致认同的基本构建模块，比较像的两个是：

	* Leader 选举
	* 分布式状态机复制

6. 对分布式系统的理解 一时仍难以有个眉目，可以多读读作者推荐的基本书。

其实上图换个 视角就成了

![](/public/upload/architecture/system_architecture_design.png)

## 弹力设计

![](/public/upload/architecture/zuoerduohaozi_resiliency.png)

无状态的服务 与 函数式编程如出一辙。为做成无状态的服务，需要耦合第三方有状态的存储服务，第三方存储服务计算与存储分离，最终依赖一个分布式文件系统。

design for failure，不要尝试着去避免故障，而是要把处理故障的代码（自我保护、打印更多信息）当成正常的功能做在架构里写在代码里。

1. 限流应该让后端服务感知到，限流发生时，我们应该在协议头中塞进一个标识，比如Http Header中放入一个限流级别，这样后端服务可以根据这个标识决定是否做降级。进一步网关要向请求中塞入链路分析的标识、全链路压测的标识、限流的标识。
2. 对于一个api或rpc，服务除提供全功能实现外，最好提供猴版实现，供调用选择
3. 前端/客户端 感知到降级（特殊字段标识）后，部分数据不展示

design for ops，比如一个服务的多个实例，分别代表处于开发状态和稳定状态的服务。开发状态可以访问稳定状态的服务，稳定状态的服务不可以访问开发状态的服务。

![](/public/upload/architecture/zuoerduohaozi_springcloud_k8s.png)

限流是api 维度的，降级是服务维度的，有时不想让某个服务的问题导致整个api不可用

**像熔断降级这些东西，我们现在看待它们还处于“神器”范畴，后续必然随着分布式的普及， 成为一个“基础知识”，进而被内化到框架中。**

## 管理设计

![](/public/upload/architecture/zuoerduohaozi_distribute_manage.png)

程序=控制+逻辑，同理架构=控制+逻辑（业务服务），边车模式优点便在于控制与逻辑隔离，sidecar 与应用可以独立升级

![](/public/upload/architecture/zuoerduohaozi_sidecar.JPG)

我们在sidecar 之上think big一下，假设在一个分布式系统中，在每个节点上都已经把一些标准的sidecar 给部署好了，那么真实的业务只需要往这个节点中放，就可以和本地的sidecar 通信，然后由sidecar 委托代理和其它系统的交互和控制。

A service mesh is a dedicated infrastructure layer for handling service-to-service communication. It’s responsible for the reliable delivery of requests through the complex topology of services that comprise a modern, cloud native application. In practice, the service mesh is typically implemented as an array of lightweight network proxies that are deployed alongside application code, without the application needing to be aware.

## 高性能

![](/public/upload/architecture/zuoerduohaozi_high_performance.png)



## 编程范式

参见[java 语言的动态性](http://qiankunli.github.io/2018/08/15/java_dynamic.html)  [函数式编程](http://qiankunli.github.io/2018/09/12/functional_programming.html) [面向对象设计](http://qiankunli.github.io/2018/10/01/object_oriented.html) [《编程的本质》笔记](http://qiankunli.github.io/2018/07/14/nature_of_code.html)

## 程序猿练级攻略

![](/public/upload/architecture/zuoerduohaozi_programmer_improvement.png)

1. 广度的知识是深度研究的副产品
2. 很多时候，你缺少的不是知识而是热情
3. 很多东西在概念上是相通的，在哲学层次上是相通的，这是你需要去追求的学习知识的境界。
4. 永远和高手一起工作
5. 不要只寄望于在工作中学习，工作没有覆盖的地方你就不学了。真正的高手在工作之余都会花很多时间去自己研究点东西的。
6. 在合适的技术而不是熟悉的技术上工作


[Teach Yourself Programming in Ten Years](http://norvig.com/21-days.html)

A language that doesn't affect the way you think about programming, is not worth knowing. 

The key is deliberative practice: not just doing it again and again, but challenging yourself with a task that is just beyond your current ability, trying it, analyzing your performance while and after doing it, and correcting any mistakes. Then repeat. And repeat again.

Learning by Doing,he most effective learning requires a well-defined task with an appropriate difficulty level for the particular individual, informative feedback, and opportunities for repetition and corrections of errors.

**Talk with other programmers; read other programs. This is more important than any book or training course.** 多与人聊天，多看代码是多么的重要。

Computer science education cannot make anybody an expert programmer any more than studying brushes and pigment can make somebody an expert painter

Learn at least a half dozen programming languages. Include one language that emphasizes class abstractions (like Java or C++), one that emphasizes functional abstraction (like Lisp or ML or Haskell), one that supports syntactic abstraction (like Lisp), one that supports declarative specifications (like Prolog or C++ templates), and one that emphasizes parallelism (like Clojure or Go).

Remember that there is a "computer" in "computer science". Know how long it takes your computer to execute an instruction, fetch a word from memory (with and without a cache miss), read consecutive words from disk, and seek to a new location on disk.


Approximate timing for various operations on a typical PC:

|||
|---|---|
|execute typical instruction|	1/1,000,000,000 sec = 1 nanosec|
|fetch from L1 cache memory|	0.5 nanosec|
|branch misprediction|	5 nanosec|
|fetch from L2 cache memory|	7 nanosec|
|Mutex lock/unlock|	25 nanosec|
|fetch from main memory|	100 nanosec|
|send 2K bytes over 1Gbps network	|20,000 nanosec|
|read 1MB sequentially from memory|	250,000 nanosec|
|fetch from new disk location (seek)|	8,000,000 nanosec|
|read 1MB sequentially from disk	|20,000,000 nanosec|
|send packet US to Europe and back	|150 milliseconds = 150,000,000 nanosec|



[97-things-every-programmer-should-know](https://github.com/97-things/97-things-every-programmer-should-know/blob/master/en/SUMMARY.md)


## 面试

好简历是要用自己的经历去写的，最牛逼的简历只有一句话：我发明了Unix

1. 技术知识的准备

	* 知识点
		* 编程语言
		* 系统知识
	* 算法题
2. 工作项目的准备
3. 为什么离职、职业规划、你的缺点是什么、你对我们有什么问题

没事面试一下， 是提高自我认知、社会认知、行业认知的重要方式。

## 高效沟通

talk 并不cheap，人与人之间talk 是直接交流，code 是间接交流（code是人与机器的直接交流）

1. 提前统一术语
2. 反馈，把你理解的说给我听
3. 用低级知识讲给没有背景知识的人
4. 信息在传递过程中的损失。公司层级越深越容易失真

![](/public/upload/architecture/zuoerduohaozi_communication.png)

另外一个地方看到的：在一个复杂环境下，很多问题已经不能就事论事来研究和解决，非常需要系统性的方法和战略性的眼光。

西方很多职业化的专家， 做任何事情都有方法论、有套路，甚至于如何开一个会都有很多套路。

## 高效学习

![](/public/upload/architecture/zuoerduohaozi_study.png)

在总结和归纳中，积累的知识越多，在知识间进行联系和区别的能力越强，总结和归纳的能力越强/轻松，进而形成在更高维度上思考问题的能力。

## 其它

![](/public/upload/architecture/zuoerduohaozi_machine_learning.png)


![](/public/upload/architecture/zuoerduohaozi_project_ability.png)



	
![](/public/upload/architecture/zuoerduohaozi_post.JPG)

个人微信订阅号

![](/public/upload/qrcode_for_gh.jpg)