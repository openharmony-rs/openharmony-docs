# Comparison Between TaskPool and Worker
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->


TaskPool and Worker provide a multithreaded runtime environment for applications, allowing them to handle time-consuming computing tasks or resource intensive tasks, preventing tasks from blocking the host thread, and improving system performance and resource utilization.


This topic compares TaskPool and Worker based on their [implementation characteristics](#implementation-characteristics-comparison) and [suitable use cases](#use-case-comparison).


## Implementation Characteristics Comparison

**Table 1** Comparison between TaskPool and Worker in implementation characteristics

| Item| TaskPool | Worker |
| -------- | -------- | -------- |
| Memory model| Threads are isolated from each other, and memory is not shared.| Threads are isolated from each other, and memory is not shared.|
| Parameter passing mechanism| The structured clone algorithm is used for serialization and deserialization.<br>ArrayBuffer, SharedArrayBuffer, and Sendable are supported.| The structured clone algorithm is used for serialization and deserialization.<br>ArrayBuffer, SharedArrayBuffer, and Sendable are supported.|
| Parameter passing| Parameters are directly passed without being encapsulated.| The message object should be encapsulated as a unique parameter.|
| Method invocation| Directly pass and call methods decorated with @Concurrent.| Messages are parsed in the Worker thread to invoke the corresponding methods.|
| Return value| Results are returned asynchronously by default.| Messages must be proactively sent and parsed by calling **onmessage()** for value assignment.|
| Lifecycle management| TaskPool automatically manages its lifecycle, without considering task load.| You need to manage the number and lifecycle of Worker threads.|
| Maximum number of tasks| The number is automatically managed, rather than being manually configured.| A maximum of 64 Worker threads can run simultaneously in the same process. The actual number is determined by the process memory.|
| Maximum task duration| 3 minutes (excluding time spent on Promise and async/await calls, such as network downloads and file read/write operations). There is no upper limit on the duration of continuous tasks.| There is no limit.|
| Task priority setting| Setting the task priority is supported.| Since API version 18, the Worker thread priority can be configured.|
| Task cancellation| Supported.| Not supported.|
| Thread reuse| Supported.| Not supported.|
| Delayed task execution| Supported.| Not supported.|
| Task dependency setting| Supported.| Not supported.|
| Serial queue| Supported.| Not supported.|
| Task group| Supported.| Not supported.|
| Periodic task| Supported.| Not supported.|
| Asynchronous queue| Supported.| Not supported.|


## Use Case Comparison

Both TaskPool and Worker support multithreaded concurrency. However, worker threads of the TaskPool are bound to the system scheduling priority and support load balancing (automatic scaling), making it more efficient than Worker, which requires manual creation and may incur delays. Therefore, TaskPool is recommended for most scenarios.

TaskPool is oriented to independent tasks, which are executed within threads. You do not need to care about the thread lifecycle, because long-running tasks (over 3 minutes and not classified as continuous tasks) are automatically reclaimed by the system. Worker applies to tasks that occupy threads for a long time. The thread lifecycle needs to be managed proactively.

Common use cases are as follows:

- Tasks exceeding 3 minutes: For tasks that run longer than 3 minutes (excluding time spent on Promise and async/await calls, such as network downloads and file I/O operations), use Worker. For example, use Worker for a background CPU-intensive prediction algorithm that runs for an hour. For details about the scenario example, see [Resident Task Development](resident-task-guide.md).

- Associated synchronous tasks: In scenarios where a series of synchronous tasks is required, such as when creating and using handles that must be permanently stored, Worker is recommended to ensure proper management of these handles. For details, see [Using Worker for Interdependent Synchronous Tasks](sync-task-development.md#using-worker-for-interdependent-synchronous-tasks).

- Tasks requiring priority setting: In versions earlier than API version 18, Worker does not support setting scheduling priorities, so TaskPool is necessary. Since API version 18, Worker supports priority settings, allowing you to choose between TaskPool and Worker based on your use case and task characteristics. For example, in a [histogram rendering scenario](cpu-intensive-task-development.md#using-taskpool-for-image-histogram-processing), background calculations for histogram data that affect user experience should be prioritized. This requires the use of TaskPool.

- Frequently canceled tasks: For tasks that need to be canceled often, such as in a Gallery viewing scenario where images on either side of the current image are cached, TaskPool is recommended to efficiently manage the cancellation of a cache task when swiping to the next image.

- Numerous or dispersed tasks: For applications with multiple modules containing numerous time-consuming tasks, using Worker for load management may be inconvenient. TaskPool is recommended in such cases. For details about the scenario example, see [Batch Database Operations](batch-database-operations-guide.md).
