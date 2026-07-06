# 应用多线程开发概述 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

在ArkTS-Sta应用开发中，多线程开发主要用于将耗时计算、密集I/O、同步调度、长时任务或常驻任务从当前线程拆分出去执行，避免阻塞当前线程并提升资源利用率。

ArkTS-Sta并发能力基于任务调度能力和共享内存模型实现。与ArkTS-Dyn不同，ArkTS-Sta不使用@Concurrent装饰TaskPool任务函数，不需要@Sendable表达共享对象，也不需要通过Worker线程文件创建后台线程。静态多线程开发主要使用[TaskPool简介 (ArkTS-Sta)](arkts-sta-taskpool-introduction.md)和[EAWorker简介 (ArkTS-Sta)](eaworker-introduction.md)。

常见业务场景可分为以下几类：

| 场景 | 推荐能力 | 说明 |
| -------- | -------- | -------- |
| 耗时任务 | TaskPool或EAWorker | 包含较大计算量、多次I/O读写或同步调度的任务。 |
| 长时任务 | TaskPool LongTask | 任务执行时间较长，但仍以一次任务执行为主。 |
| 常驻任务 | EAWorker | 需要跟随业务生命周期长期存在，持续接收消息或维护线程上下文。 |

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 静态如何解决动态场景

动态ArkTS文档中的多线程开发场景通常基于TaskPool和Worker。迁移到ArkTS-Sta时，需要根据静态并发模型调整实现方式。

| 动态场景写法 | ArkTS-Sta写法 |
| -------- | -------- |
| 使用@Concurrent标记TaskPool任务函数。 | 普通函数可直接作为TaskPool任务函数。 |
| 从@kit.ArkTS导入taskpool。 | taskpool为静态标准库能力，示例中直接使用。 |
| 使用Worker线程文件和postMessage通信。 | 使用EAWorker创建独占线程，通过run、postToMain、MessageHandler和Message通信。 |
| 使用Sendable对象或SharedArrayBuffer提升跨线程传递效率。 | ArkTS-Sta对象默认共享。多线程读写可变对象时使用锁、原子类型或并发容器。 |
| Worker调用宿主线程注册对象。 | 使用EAWorker.postToMain或面向目标EAWorker的MessageHandler显式调用。 |

## 任务类型选择

- [耗时任务并发场景简介 (ArkTS-Sta)](arkts-sta-time-consuming-task-overview.md)：说明CPU密集型、I/O密集型和同步任务的分类。
- [CPU密集型任务开发指导（TaskPool和EAWorker） (ArkTS-Sta)](arkts-sta-cpu-intensive-task-development.md)：独立计算优先使用TaskPool，需要长期保留模型状态时使用EAWorker。
- [I/O密集型任务开发指导（TaskPool） (ArkTS-Sta)](arkts-sta-io-intensive-task-development.md)：密集文件读写、网络请求等任务可通过TaskPool调度到后台线程执行。
- [同步任务开发指导（TaskPool和EAWorker） (ArkTS-Sta)](arkts-sta-sync-task-development.md)：独立同步任务使用TaskPool，关联状态或固定线程上下文使用EAWorker。
- [长时任务开发指导（TaskPool） (ArkTS-Sta)](arkts-sta-long-time-task-guide.md)：使用LongTask处理一次长时任务，并通过共享标志或业务事件结束任务。
- [常驻任务开发指导（EAWorker） (ArkTS-Sta)](arkts-sta-resident-task-guide.md)：使用EAWorker维护长期运行的后台任务。
- [应用多线程开发实践案例概述 (ArkTS-Sta)](arkts-sta-multithread-develop-case-overview.md)：说明动态多线程实践案例在ArkTS-Sta中的迁移策略。

## 使用建议

- 优先使用TaskPool处理短时、独立、可拆分或批量任务。
- 需要固定线程、长期驻留、独立事件循环或线程内状态复用时，使用EAWorker。
- 多线程共享可变数据前先设计同步策略，避免数据竞争。
- 需要拷贝语义时显式拷贝对象或数组，不要依赖TaskPool隐式克隆。
- 使用EAWorker后，应在不再需要时调用join或quit释放线程资源。
