# 耗时任务并发场景简介 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

耗时任务是指执行时间较长、可能阻塞当前线程的任务。如果在UI主线程或关键业务线程直接执行，可能导致响应延迟、卡顿或掉帧。ArkTS-Sta中，耗时任务通常通过[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)或[EAWorker（独占线程任务执行器）(ArkTS)](../reference/apis-arkts/eaworker_managed.md)放到后台线程执行。

典型耗时任务包括CPU密集型任务、I/O密集型任务和同步任务。

| 常见业务场景 | 具体业务描述 | 是否为CPU密集型任务 | 是否为I/O密集型任务 | 是否为同步任务 |
| -------- | -------- | -------- | -------- | -------- |
| 图片/视频编解码 | 将图片或视频进行编解码再展示。 | 是 | 是 | 否 |
| 压缩/解压缩 | 解压本地压缩包或压缩本地文件。 | 是 | 是 | 否 |
| JSON解析 | 序列化和反序列化JSON字符串。 | 是 | 否 | 否 |
| 模型运算 | 对数据进行模型运算分析。 | 是 | 否 | 否 |
| 网络下载 | 密集网络请求下载资源、图片、文件等。 | 否 | 是 | 否 |
| 数据库操作 | 写入或读取数据库数据，例如聊天记录、音乐列表、页面布局信息等。 | 否 | 是 | 否 |
| 多步骤顺序处理 | 一组任务需要按顺序执行或共享同一上下文。 | 视业务而定 | 视业务而定 | 是 |

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 能力选择

| 任务类型 | 推荐能力 | 说明 |
| -------- | -------- | -------- |
| CPU密集型任务 | TaskPool或EAWorker | 独立、可拆分任务优先使用TaskPool；需要长期保留模型状态或固定线程上下文时使用EAWorker。 |
| I/O密集型任务 | TaskPool | 将密集I/O调度到后台线程，减少对当前线程的阻塞。 |
| 同步任务 | TaskPool或EAWorker | 相互独立的同步任务可使用TaskPool；有关联状态或同一句柄的任务可使用EAWorker。 |

## 与ArkTS-Dyn写法的差异

- ArkTS-Sta普通函数可作为TaskPool任务函数，不需要@Concurrent。
- ArkTS-Sta对象默认跨线程共享，不需要@Sendable。
- ArkTS-Sta不使用Worker线程文件处理长期后台任务，需要独占线程时使用EAWorker。
- 共享可变数据需要使用锁、原子类型或并发容器保证线程安全。

后续章节将分别介绍[CPU密集型任务开发指导（TaskPool和EAWorker） (ArkTS-Sta)](arkts-sta-cpu-intensive-task-development.md)、[I/O密集型任务开发指导（TaskPool） (ArkTS-Sta)](arkts-sta-io-intensive-task-development.md)和[同步任务开发指导（TaskPool和EAWorker） (ArkTS-Sta)](arkts-sta-sync-task-development.md)的开发方式。
