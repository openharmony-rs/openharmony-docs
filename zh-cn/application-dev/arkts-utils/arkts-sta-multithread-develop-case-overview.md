# 应用多线程开发实践案例概述 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

ArkTS-Sta应用多线程开发实践案例用于说明如何将动态ArkTS中的TaskPool、Worker、Sendable等并发场景迁移到静态并发模型。ArkTS-Sta基于任务调度能力和共享内存模型实现，并发任务主要通过[TaskPool简介 (ArkTS-Sta)](arkts-sta-taskpool-introduction.md)和[EAWorker简介 (ArkTS-Sta)](eaworker-introduction.md)承载。

与动态ArkTS相比，ArkTS-Sta不需要使用@Concurrent装饰TaskPool任务函数，也不需要使用@Sendable声明跨线程共享对象。对象、数组和ArrayBuffer默认按共享引用在线程间传递；当多个线程读写同一份可变数据时，需要使用锁、原子类型或并发容器保护。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 静态如何解决动态场景

| 动态ArkTS常见写法 | ArkTS-Sta处理方式 |
| -------- | -------- |
| 使用@Concurrent标记TaskPool任务函数。 | 普通函数可以直接作为TaskPool任务函数，也可以封装为taskpool.Task后执行。 |
| 从@kit.ArkTS导入taskpool。 | taskpool为ArkTS-Sta内置并发能力，示例中直接使用。 |
| 使用Worker线程文件和postMessage通信。 | 使用EAWorker创建独占线程，通过run、postToMain、MessageHandler和Message通信。 |
| 使用Sendable或Sendable容器减少跨线程拷贝。 | ArkTS-Sta对象默认共享。需要快照语义时显式拷贝；共享可变对象需要同步保护。 |
| 使用Transferable转移ArrayBuffer所有权。 | ArkTS-Sta默认共享对象引用。若业务要求互不影响，应创建新的ArrayBuffer或数组副本。 |
| 多个任务并发写同一份外部状态。 | 根据外部资源特性选择锁、并发容器、SequenceRunner或固定EAWorker串行处理。 |

## 案例列表

- [批量数据写数据库场景 (ArkTS-Sta)](arkts-sta-batch-database-operations-guide.md)：使用TaskPool将数据库创建、批量写入、查询和清理放到后台线程执行；大批量写入时通过数据快照和SequenceRunner控制写入顺序。
- [业务模块并发加载场景 (ArkTS-Sta)](arkts-sta-concurrent-loading-modules-guide.md)：使用TaskPool并发初始化多个独立业务模块，并在宿主线程汇总初始化结果。
- [全局配置项功能场景 (ArkTS-Sta)](arkts-sta-global-configuration-guide.md)：使用模块级单例保存进程内共享配置，并通过锁保护多线程读写。
- [ArkUI数据更新场景 (ArkTS-Sta)](arkts-sta-arkui-data-update.md)：后台线程生成普通数据，宿主线程通过makeObserved或@ObservedV2更新UI状态。
- [TaskPool指定任务并发度场景 (ArkTS-Sta)](arkts-sta-taskpool-async-task-guide.md)：使用AsyncRunner限制同类任务并发度，并通过等待队列容量控制任务堆积。
- [ArkUI瀑布流渲染场景 (ArkTS-Sta)](arkts-sta-taskpool-waterflow.md)：使用TaskPool后台查询或预处理数据，宿主线程追加到WaterFlow数据源并增量刷新。
- [获取最近访问列表场景 (ArkTS-Sta)](arkts-sta-lrucache-recent-list.md)：使用LRUCache维护最近访问顺序，并通过锁保护多线程访问。
- [多线程取消TaskPool任务场景 (ArkTS-Sta)](arkts-sta-multi-thread-cancel-task.md)：通过任务ID在另一个TaskPool任务中取消目标任务，并在运行中任务内主动检查取消状态。
- [Native资源显式移交场景 (ArkTS-Sta)](arkts-sta-native-resource-transfer.md)：使用Native句柄和显式移交协议表达所有权转移。
- [Native共享资源多线程操作场景 (ArkTS-Sta)](arkts-sta-native-shared-resource.md)：使用共享Native句柄和C++锁保护多线程访问。
- [EAWorker常驻线程通过TaskPool进行多任务并发处理 (ArkTS-Sta)](arkts-sta-worker-and-taskpool.md)：使用EAWorker作为常驻调度线程，并将多个独立子任务提交给TaskPool并发执行。
- [C++线程间数据共享场景 (ArkTS-Sta)](arkts-sta-native-interthread-shared.md)：使用ANI绑定静态Native方法，并在C++线程附加ArkTS运行环境后访问ArkTS能力。

## 使用建议

- 迁移动态TaskPool示例时，先移除@Concurrent和@kit.ArkTS导入，再检查任务函数参数和返回值是否符合ArkTS-Sta的静态类型约束。
- 迁移Sendable示例时，不要直接保留@Sendable、collections.Array等动态并发写法。ArkTS-Sta中应明确数据是共享、只读快照还是受同步保护的可变状态。
- 多线程访问数据库、文件、网络连接等外部资源时，需要结合对应API的线程安全约束设计任务边界。无法确认API是否允许后台线程调用时，应优先查询对应接口文档或源码实现。
- 对于短时、独立、可拆分的任务，优先使用TaskPool；对于需要固定线程、常驻状态或长期监听的任务，使用EAWorker。
