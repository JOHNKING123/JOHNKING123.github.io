---

layout: post
title: jib源码分析之细节
category: 技术
tags: Docker
keywords: jib

---

## 简介（持续更新）

* TOC
{:toc}

阅读本文前，建议事先了解下 [jib源码分析及应用](http://qiankunli.github.io/2018/11/19/jib_source.html)

### 几个问题

通过docker registry v2 api，是可以上传镜像的

1. jib 的最后，是不是也是调用 docker registry v2 api？ 比如对于golang语言 就有针对 registry api 的库 [github.com/heroku/docker-registry-client](https://github.com/heroku/docker-registry-client)
3. jib maven plugin 与 jib-core 分工的边界在哪里？ 直接的代码调用，使用jib-core 即可
1. 如何将不同的数据分layer
2.  [jib源码分析及应用](http://qiankunli.github.io/2018/11/19/jib_source.html) 的分析只涉及到 jib 有限的几个package，还有大量package 分别是什么作用？
3. Allocation 看着很复杂，是什么意思？
4. TimerEventDispatcher 为什么有这个？
5. guava Futures 的深意要好好理解


## EventDispatcher

在`com.google.cloud.tools.jib.event`包下 有几个类


1. DefaultEventDispatcher
2. EventDispatcher
3. EventHandlers
4. Handler
5. JibEvent
6. JibEventType
7. events 定义了几个特定的JibEvent，比如LogEvent、ProgressEvent、TimerEvent

详情如下

	public interface EventDispatcher {
	  	void dispatch(JibEvent jibEvent);
	}

	public interface JibEvent {}
	
	class Handler<E extends JibEvent> {
		private final Class<E> eventClass;
		// java8 java.util.function. Consumer
		private final Consumer<E> eventConsumer;
		Handler(Class<E> eventClass, Consumer<E> eventConsumer) {
			this.eventClass = eventClass;
			this.eventConsumer = eventConsumer;
		}
		void handle(JibEvent jibEvent) {
			Preconditions.checkArgument(eventClass.isInstance(jibEvent));
			// Class.cast 强转的简便用法
			eventConsumer.accept(eventClass.cast(jibEvent));
		}
	}
	// Handler工具类
	public class EventHandlers {...}
	
	public class DefaultEventDispatcher implements EventDispatcher {
		private final ImmutableMultimap<Class<? extends JibEvent>, Handler<? extends JibEvent>> handlers;
			public DefaultEventDispatcher(EventHandlers eventHandlers) {
			handlers = eventHandlers.getHandlers();
		}
		@Override
		public void dispatch(JibEvent jibEvent) {
			handlers.get(JibEvent.class).forEach(handler -> handler.handle(jibEvent));
			handlers.get(jibEvent.getClass()).forEach(handler -> handler.handle(jibEvent));
		}
	}



设置EventHandler 的方式

    containerizer
        .getEventHandlers()
        .ifPresent(
            eventHandlers ->
                buildConfigurationBuilder.setEventDispatcher(
                    new DefaultEventDispatcher(eventHandlers)));


1. 定义一套event 生产与消费 的接口约定
1. 框架流程持有EventDispatcher 在恰当的时机发布event。所以对于jib来说，只关心EventDispatcher 和 event。EventDispatcher 之所以带 Dispatcher 是因为其会根据event 类型分发
2. 传统的观察者模式，Subject 会直接持有 Observer列表，而在jib 中，EventDispatcher ==> Handler ==> Consumer 三角关系。为何呀？一个重要因素是JibEvent 定义了不同的事件类型，如果还是 Subject-Observer 二元关系。则Subject 要么定义不同的方法，用来分发不同的事件；要么一个分发方法中实现if else，Observer 作为事件接收方法类似。
3. 真正的 event 源 聚合了EventDispatcher 而不是 实现它。
3. 但万变不离其宗，从`new DefaultEventDispatcher(eventHandlers)`看， 还是通过 “Observer” 去构造“Subject”

[函数式编程对设计模式的影响](http://qiankunli.github.io/2018/09/12/functional_programming.html)

## Allocation

在`com.google.cloud.tools.jib.event.progress`包下

### 创建

![](/public/upload/docker/jib_Allocation.png)

Allocation 有两个创建入口：newRoot 和 newChild。newChild 分散在各个 Step 中被调用。

newRoot 的创建入口在 StepsRunner 中

	private void createRootProgressAllocation(String description) {
		rootProgressAllocation = Allocation.newRoot(description, stepsCount);
		buildConfiguration.getEventDispatcher().dispatch(new ProgressEvent(rootProgressAllocation, 0L));
	}

并且createRootProgressAllocation只在 以下三个方法中使用，它们分别是 forBuildToDockerRegistry、forBuildToDockerDaemon、forBuildToTar 的finalStep

1. StepsRunner.pushImage
2. StepsRunner.loadDocker
3. StepsRunner.writeTarFile


在将finalStep 时创建rootProgressAllocation，然后从第一个Step 开始 真正执行 流程。Step真正开始运行时（执行子Step的构造方法）会检查 是否有rootProgressAllocation

### 基本概念

1. Decentralized Allocation Tree (DAT)
2. Allocation，A DAT node is immutable and pointers only go in the direction from child to parent. java 里面表示一个tree、链表、队列 都只 表示一个Node 就行了。
2. allocation unit，从`StepsRunner.createRootProgressAllocation` 可以看到，rootProgressAllocation 的allocation unit 为step 的数量。而非finalStep 的allocation 的 allocation unit 都为1（不准确）。
3. fractionOfRoot

加上非finalStep代码中 频频出现 progressAllocation ，可以做一个大胆假设：allocation 是用来跟踪进度的。

如果看过[jib源码分析及应用](http://qiankunli.github.io/2018/11/19/jib_source.html) 中的Step 依赖关系图，并可以知道，感知一个并行的任务的进度是非常困难的。因为对Decentralized Allocation Tree 了解不多，本文不做过多涉及。


## future


对future的理解

1. [彻底理解Java的Future模式](https://www.cnblogs.com/cz123/p/7693064.html) 单线程就不说了，在多线程中，你另起线程执行一个任务，Runnable.run 是没有返回值的。**从调用方的角度看，另起线程是为了加快处理，不意味着不关心执行结果。 调用方可以先不管 返回结果干别的，但不意味着永远不关心返回结果。所以调用方要有获取返回结果的手段，甚至于影响执行线程的手段（比如取消）。** 了解了这个，就会对那么多future的扩充类找到感觉，因为它们都是从调用者需求出发的。
2. [Interface Future<V>](https://docs.oracle.com/javase/7/docs/api/java/util/concurrent/Future.html) A Future represents the result of an asynchronous computation. 
3. [Guide to java.util.concurrent.Future](https://www.baeldung.com/java-future)future 一般与Callable 和ExecutorService 结合使用。  Callable is an interface representing a task that returns a result and has a single call() method. Creating an instance of Callable does not take us anywhere, we still have to pass this instance to an executor that will take care of starting that task in a new thread and give us back the valuable Future object. That’s where ExecutorService comes in.
4. 自己的理解：凡是异步，必涉及调用方和执行方（通常还有队列），两方必涉及沟通媒介，类似于“句柄” 之类的东东。


## 一些Step的实现原理

以常用 的forBuildToDockerRegistry 包含的步骤来分析

### retrieveTargetRegistryCredentialsStep

这个步骤的本质是 获取Credential ，也就是用户名和密码，无需远程访问。


	class RetrieveRegistryCredentialsStep implements AsyncStep<Credential>, Callable<Credential> {
	  	public Credential call() throws CredentialRetrievalException {
	  		...
	  		Optional<Credential> optionalCredential = credentialRetriever.retrieve();
	  		...
	  	}	
	}
	
	@FunctionalInterface
	public interface CredentialRetriever {
	  	Optional<Credential> retrieve() throws CredentialRetrievalException;
	}
	
CredentialRetriever 是构建 RegistryImage	时拿到的

	public class RegistryImage implements SourceImage, TargetImage {
		public RegistryImage addCredential(String username, String password) {
	    	addCredentialRetriever(() -> Optional.of(Credential.basic(username, password)));
	    	return this;
	  	}
	}
	
	public class Credential {
		private final String username;
  		private final String password;
	}

个人微信订阅号

![](/public/upload/qrcode_for_gh.jpg)