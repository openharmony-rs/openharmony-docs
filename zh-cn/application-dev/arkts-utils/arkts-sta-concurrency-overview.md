# 静态并发概述
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

ArkTS-Dyn已经提供了Sendable对象来实现跨线程共享能力，但也是基于内存隔离的基础上，实现的部分数据共享。不能实现主流编程语言并发的内存共享模型。

ArkTS-Sta则实现了共享内存模型，跨线程传递的时候不需要定义Structured Clone，Sendable对象表达共享语义， 对象可以直接在线程间共享。共享内存降低了跨线程传递成本，也要求开发者在多线程读写共享可变数据时显式使用锁、原子类型或并发容器保证线程安全。

ArkTS-Sta提供了和ArkTS-Dyn类似的并发接口，可以方便的让开发者从动态代码转移到静态代码。
- 提供了Promise和async/await编排异步流程
- 使用TaskPool将后台任务提交到运行时管理的工作线程执行
- 提供了EAWorker来实现和ArkTS-Dyn Worker同样的功能，可以让在EAWorker上创建的任务都在这个EAworker上调度

此外，ArkTS-Sta提供了如下能力来保障数据并发安全
- 锁：解决共享数据的数据竞争
- 原子类型：解决维护单值状态的数据竞争
- Worker Local：解决工作线程间数据隔离问题
- 并发容器： 并发安全易用的数据结构

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 并发能力构成

| 能力 | 说明 | 适用场景 |
| -------- | -------- | -------- |
| Promise和async/await | 用Promise表示异步结果，通过await等待异步操作完成。 | I/O等待、定时器或异步流程编排。 |
| TaskPool | 将短时或可拆分任务提交到运行时管理的任务池执行，并通过Promise返回结果。 | CPU密集型计算、后台数据处理或批量任务。 |
| EAWorker | 创建独占工作线程，并在该线程上提交任务。 | 固定线程、长期驻留、独立事件循环或与JS互操作。 |
| 线程间通信 | 通过共享内存、TaskPool结果和进度通知、EAWorker消息等方式在线程间协作。 | 数据共享、任务通知或主线程与工作线程协同。 |
| 并发数据安全| 使用锁、原子类型、并发容器或WorkerLocal管理共享数据。 | 多线程读写共享对象、生产者/消费者或线程本地状态。 |

## 并发任务调度模型

ArkTS-Sta中的async函数、Promise回调、TaskPool任务和EAWorker任务都可以作为并发任务参与调度。运行时根据任务类型、目标工作线程和调度策略执行任务。

并发任务调度的核心特点如下：

- 一个工作线程可以按调度策略执行多个任务。如果当前任务等待异步事件时挂起，当前工作线程可以继续处理其他就绪任务。
- 多个工作线程可以并行执行不同任务。CPU密集型任务可以通过TaskPool能力把多个任务分发到后台工作线程上执行。
- EAWorker对应独占工作线程。所有的任务都在当前EAWorker上执行
- TaskPool由运行时管理工作线程和任务队列。开发者只需要提交任务，而不需要对线程的生命周期进行管理
- ArkTS-Sta的共享数据在多个线程并行访问同一可变对象时，仍需使用锁、原子类型或并发容器的保护。

## 异步并发

Promise用于表示异步操作的最终状态和结果。async函数返回Promise，await会暂停当前async函数后续执行，等待Promise完成后继续执行。

异步并发主要解决等待和流程编排问题，不会自动把计算密集型代码切换到其他线程。如果同步计算耗时较长，应使用TaskPool或EAWorker将任务提交到后台线程执行。

详细用法请参见[异步并发 (Promise和async/await)](arkts-sta-async-concurrency-overview.md)。

## 多线程并发

TaskPool适合执行短时、可拆分或可批量调度的任务。开发者可以直接提交函数，也可以构造Task、TaskGroup、SequenceRunner或AsyncRunner组织任务。TaskPool返回Promise表示任务执行结果。

EAWorker适合需要独占线程的场景。开发者可以创建EAWorker并启动其工作线程，再通过run向该线程提交任务。与TaskPool相比，EAWorker需要开发者显式管理启动和退出，更适合长期驻留或有固定线程语义的任务。

详细说明请参见[静态TaskPool简介](arkts-sta-taskpool-introduction.md)和[静态TaskPool和EAWorker的对比 (TaskPool和EAWorker)](arkts-sta-taskpool-vs-worker.md)。

## 线程间通信和数据共享

共享内存降低了跨线程传递成本，但也要求开发者明确数据访问规则。只读数据可以直接共享；可变数据存在多线程读写时，需要使用以下方式保证一致性：

- Mutex、RWLock保证数据安全
- 使用AtomicInt、AtomicBoolean等原子类型维护单值状态。
- 使用ConcurrentHashMap、ConcurrentSet或BlockingQueue等并发容器管理集合数据。
- 使用WorkerLocal保存线程本地状态，减少共享数据。

详细说明请参见[静态线程间通信概述](arkts-sta-interthread-communication-overview.md)和[静态并发数据共享](arkts-sta-data-sharing-for-concurrency.md)。

## 与ArkTS-Dyn并发的主要差异

ArkTS-Sta并发能力与ArkTS-Dyn在概念上相近，但在数据模型、接口约束和任务写法上存在差异。

| 差异点 | ArkTS-Sta |
| -------- | -------- |
| 任务函数 | 普通函数可作为TaskPool任务函数，不需要@Concurrent装饰。 |
| 共享对象 | 对象默认可跨线程共享，不需要@Sendable装饰。 |
| 数据传递 | 不提供TaskPool的setCloneList和setTransferList接口，需要拷贝语义时应显式创建副本。 |
| Worker能力 | 使用EAWorker表示ArkTS-Sta独占工作线程能力。 |
| 同步责任 | 共享可变数据时，开发者需要自行使用锁、原子类型或并发容器保证并发安全。 |

## 使用建议

- I/O等待和异步流程编排优先使用Promise和async/await。
- CPU密集型、可拆分或短时后台任务优先使用TaskPool。
- 需要固定线程、长期驻留或独立事件循环时使用EAWorker。
- 多线程共享可变数据前先设计同步策略，不要把共享内存等同于线程安全。
- 需要独立快照时显式拷贝对象或数组，避免任务修改原始数据。
- 高频共享集合优先使用并发容器，单值状态优先使用原子类型。
