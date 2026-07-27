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

Both TaskPool and Worker support multi-threaded concurrency. TaskPool worker threads are bound to the system scheduling priority and support load balancing (automatic scaling). In contrast, Worker threads need to be created and destroyed manually by developers, incurring certain costs for creation and management. Therefore, TaskPool is recommended in most scenarios.

Worker applies to scenarios where threads need to be occupied for an extended period and the thread lifecycle needs to be managed manually by developers. TaskPool applies to scenarios where relatively independent tasks are executed, and there is no need to focus on thread lifecycle when tasks run in threads.

### Recommended Scenarios for Worker

In the following scenarios, tasks usually need to run for a long time or depend on the thread context, making Worker the suitable choice:

- **Tasks with a runtime exceeding 3 minutes**

  (The 3-minute duration mentioned here does not include the time consumed by Promise and async/await asynchronous calls, such as I/O tasks like network downloads and file read/write operations):

  For example, use Worker for a background CPU-intensive prediction algorithm that runs for an hour.

  For details about the scenario example, see [Resident Task Development](resident-task-guide.md).

- **A set of related synchronous tasks**

  For example, in scenarios where handles need to be created and used, each newly created handle is unique and must be persistently retained to ensure the correct execution of subsequent operations. Such scenarios are suitable for Worker.

  For details, see [Using Worker for Interdependent Synchronous Tasks](sync-task-development.md#using-worker-for-interdependent-synchronous-tasks).

### Recommended Scenarios for Worker

In the following scenarios, tasks are typically relatively independent and have higher requirements for scheduling, cancellation, or management capabilities, making TaskPool the suitable choice:

- **Tasks requiring priority setting**

  In versions earlier than API version 18, Worker does not support setting scheduling priorities, so TaskPool is necessary.

  Since API version 18, Worker supports priority settings, allowing you to choose between TaskPool and Worker based on your use case and task characteristics. 

  For example, in a [histogram rendering scenario](cpu-intensive-task-development.md#using-taskpool-for-image-histogram-processing), the histogram data calculated in the background is used for foreground UI display (which impacts user experience), and the task is relatively independent. Therefore, TaskPool is recommended.

- **Tasks requiring frequent cancellation**

  For tasks that need to be canceled often, such as in a Gallery viewing scenario where images on either side of the current image are cached, TaskPool is recommended to efficiently manage the cancellation of a cache task when swiping to the next image.

- **Numerous or dispersed tasks**

  For applications with multiple modules containing numerous time-consuming tasks, you are advised to use TaskPool instead of Worker for load management.

  For details about the scenario example, see [Batch Database Operations](batch-database-operations-guide.md).
