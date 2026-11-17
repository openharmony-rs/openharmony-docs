---
kits: ["ArkTS / Ark Programming Language"]
description: "Overview of the ArkTS concurrency capability system: asynchronous concurrency, based on Promise and async/await, is suitable for single I/O tasks; multithreaded concurrency, based on TaskPool and Worker, is suitable for time-consuming, long-time, and resident task scenarios. It also introduces the different transfer methods of inter-thread communication objects."
keywords: [concurrency overview, asynchronous concurrency, multithreaded concurrency, Promise, TaskPool, Worker, time-consuming task, inter-thread communication]
doctype: guide
status: active
---

# Overview of Concurrency
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @huanghello-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=f8431cb42cf0d545a37a384860003cd8449b0b43 translatedAt=2026-11-06T10:29:17.818Z pushedAt=2026-11-12T02:59:04.822Z nl=1 -->

Concurrency refers to the situation where multiple tasks are executed at the same time. On a multi-core device, tasks can be executed concurrently on different CPUs. On single-core devices, while multiple tasks are not executed at the same time, the CPU can switch between tasks when one is idle or performing I/O operations, thereby optimizing CPU resource utilization.

To improve the response speed and frame rate of applications and mitigate the impact of time-consuming tasks on the UI main thread, ArkTS provides two concurrency strategies: asynchronous concurrency and multithreaded concurrency.

- Asynchronous concurrency involves pausing asynchronous code at a certain point and resuming its execution later, ensuring that only one piece of code is running at any given moment. ArkTS supports asynchronous concurrency through Promises and async/await, which are well-suited for scenarios involving single I/O operations. For details, see [Asynchronous Concurrency](async-concurrency-overview.md).

- Multithreaded concurrency allows multiple code segments to be executed concurrently. While the UI main thread continues to handle user interactions and update the UI, background threads can perform time-consuming operations, thereby preventing application lag. ArkTS supports multithreaded concurrency through TaskPool and Worker, which are ideal for scenarios involving [time-consuming tasks](time-consuming-task-overview.md). For details, see [Multithreaded Concurrency](multi-thread-concurrency-overview.md).


In multithreaded concurrency scenarios, data communication between different threads is necessary. Different types of objects may use different transfer methods, such as copy or memory sharing.

Concurrency capability is widely used in various scenarios, including [asynchronous concurrent tasks](async-concurrency-overview.md), [time-consuming tasks](time-consuming-task-overview.md) (such as [CPU-intensive tasks](cpu-intensive-task-development.md), [I/O-intensive tasks](io-intensive-task-development.md), and [synchronous tasks](sync-task-development.md)), [long-running tasks](long-time-task-overview.md), [resident tasks](resident-task-overview.md), and so on. Developers can select the appropriate concurrency strategy for optimization and development based on different task requirements and scenarios.