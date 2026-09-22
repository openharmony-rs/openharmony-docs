# @ohos.taskpool(Task Pool)

TaskPool provides a multi-thread running environment for applications. It helps reduce resource consumption and improve system performance. It also frees you from caring about the thread lifecycle. You can use the TaskPool APIs to create background tasks and perform operations on them, for example, executing or canceling a task. Theoretically, you can create an unlimited number of tasks, but this is not recommended due to memory limitations. In addition, you are not advised performing blocking operations in a task, especially indefinite blocking. Long-time blocking operations occupy worker threads and may block other task scheduling, adversely affecting your application performance. You can determine the execution sequence of tasks with the same priority. They are executed in the same sequence as you call the task execution APIs. The default task priority is MEDIUM. If the number of tasks to be executed is greater than the number of worker threads in the task pool, the task pool scales out based on load balancing to minimize the waiting duration. Similarly, when the number of tasks to be executed falls below the number of worker threads, the task pool scales in to reduce the number of worker threads. For details about the error codes returned by TaskPool APIs, see [Utils Error Codes](../../../reference/apis-arkts/errorcode-utils.md). For details about the precautions for using TaskPool, see [Precautions for TaskPool](../../../arkts-utils/taskpool-introduction.md#precautions-for-taskpool). The following concepts are used in this topic:

- Task group task: task in a [TaskGroup](arkts-arkts-taskpool-taskgroup-c.md).  
- Serial queue task: task in a [SequenceRunner](arkts-arkts-taskpool-sequencerunner-c.md).  
- Asynchronous queue task: task in an [AsyncRunner](arkts-arkts-taskpool-asyncrunner-c.md).  
- Periodic task: task executed by calling [executePeriodically](arkts-arkts-taskpool-executeperiodically-f.md).

**Since:** 9

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [cancel](arkts-arkts-taskpool-cancel-f.md#cancel) | Cancels a task in the task pool. If the task is in the internal queue of the task pool, the task will not be executed after being canceled, and an exception indicating task cancellation is returned. If the task has been distributed to the worker thread of the task pool, canceling the task does not affect the task execution, and the execution result is returned in the catch branch. You can use **isCanceled()** to check the task cancellation status. In other words, **taskpool.cancel** takes effect for calls of **taskpool.execute**, **taskpool.executeDelayed**, or **taskpool.executePeriodically**. Starting from API version 20, after performing a cancel operation, you can use the generic type BusinessError&lt;[taskpool.TaskResult](arkts-arkts-taskpool-taskresult-i.md)&gt; in the catch branch to obtain the exception information thrown by the task or the final execution result. |
| [cancel](arkts-arkts-taskpool-cancel-f.md#cancel-1) | Cancels a task group in the task pool. If a task group is canceled before all the tasks in it are finished, **undefined** is returned. Starting from API version 20, after performing a cancel operation, you can use the generic type BusinessError&lt;[taskpool.TaskResult](arkts-arkts-taskpool-taskresult-i.md)&gt; in the catch branch to obtain the exception information thrown by the task or the final execution result. |
| [cancel](arkts-arkts-taskpool-cancel-f.md#cancel-2) | Cancels a task in the task pool by task ID. If the task is in the internal queue of the task pool, the task will not be executed after being canceled, and an exception indicating task cancellation is returned. If the task has been distributed to the worker thread of the task pool, canceling the task does not affect the task execution, and the execution result is returned in the catch branch. You can use **isCanceled()** to check the task cancellation status. **taskpool.cancel** takes effect for the previous calls of **taskpool.execute** or **taskpool.executeDelayed**. If **taskpool.cancel** is called by other threads, note that the cancel operation, which is asynchronous, may take effect for later calls of **taskpool.execute** or **taskpool.executeDelayed**. Starting from API version 20, after performing a cancel operation, you can use the generic type BusinessError&lt;[taskpool.TaskResult](arkts-arkts-taskpool-taskresult-i.md)&gt; in the catch branch to obtain the exception information thrown by the task or the final execution result. |
| [execute](arkts-arkts-taskpool-execute-f.md#execute) | Places a function to be executed in the internal queue of the task pool. The function is not executed immediately. It waits to be distributed to the worker thread for execution. In this mode, the function cannot be canceled. This API uses a promise to return the result. |
| [execute](arkts-arkts-taskpool-execute-f.md#execute-1) | Verifies the passed-in parameter types and return value type of a concurrent function, and places the function in the queue of the task pool. This API uses a promise to return the result. |
| [execute](arkts-arkts-taskpool-execute-f.md#execute-2) | Places a task in the internal queue of the task pool. The task will not be executed immediately; instead, it waits to be distributed to a worker thread for execution. In the current mode, you can set the task priority and cancel the task. Note that the task cannot belong to a task group, serial queue, or asynchronous queue. For non-continuous tasks, this API can be called multiple times. This API uses a promise to return the result. |
| [execute](arkts-arkts-taskpool-execute-f.md#execute-3) | Places the generic task in the internal queue of the task pool. The parameter type and return value type of the task are not verified. This API uses a promise to return the result. The verification of the **execute** task works in conjunction with **new GenericsTask**, requiring that the parameter and return value types match those specified in **new GenericsTask**. |
| [execute](arkts-arkts-taskpool-execute-f.md#execute-4) | Places a task group in the internal queue of the task pool. The tasks in the task group are not executed immediately. They wait to be distributed to the worker thread for execution. After all tasks in the task group are executed, a result array is returned. This mode is applicable to the execution of associated tasks. This API uses a promise to return the result. |
| [execute](arkts-arkts-taskpool-execute-f.md#execute-5) | Execute a concurrent task with Configs. |
| [execute](arkts-arkts-taskpool-execute-f.md#execute-6) | Execute a concurrent generics task with Configs. |
| [execute](arkts-arkts-taskpool-execute-f.md#execute-7) | Execute a concurrent task group with Configs. |
| [executeDelayed](arkts-arkts-taskpool-executedelayed-f.md#executedelayed) | Executes a task after a given delay. In this execution mode, you can set the task priority and call **cancel()** to cancel the execution. The task cannot be a task in a task group, serial queue, or asynchronous queue, or a periodic task. This API can be called only once for a continuous task, but multiple times for a non-continuous task. This API uses a promise to return the result. |
| [executeDelayed](arkts-arkts-taskpool-executedelayed-f.md#executedelayed-1) | Executes the generic task with a delay without verifying the parameter type and return value type of the task. This API uses a promise to return the result. The verification of the **executeDelayed** task works in conjunction with **new GenericsTask**, requiring that the parameter and return value types match those specified in **new GenericsTask**. |
| [executePeriodically](arkts-arkts-taskpool-executeperiodically-f.md#executeperiodically) | Executes a task periodically. In this execution mode, you can set the task priority and call **cancel()** to cancel the execution. A periodic task cannot be a task in a task group, serial queue, or asynchronous queue. It cannot call **execute()** again or have a dependency relationship. |
| [executePeriodically](arkts-arkts-taskpool-executeperiodically-f.md#executeperiodically-1) | Executes a generic task periodically, without verifying the parameter type and return value type of the task. The verification of the **executePeriodically** task works in conjunction with **new GenericsTask**, requiring that the parameter and return value types match those specified in **new GenericsTask**. |
| [getTask](arkts-arkts-taskpool-gettask-f.md) | Obtains the corresponding task instance by task ID, or by task ID and task name. |
| [getTaskPoolInfo](arkts-arkts-taskpool-gettaskpoolinfo-f.md) | Obtains the thread information and task information of the task pool. |
| [isConcurrent](arkts-arkts-taskpool-isconcurrent-f.md) | Checks whether a function is a concurrent function. |
| [terminateTask](arkts-arkts-taskpool-terminatetask-f.md) | Terminates a continuous task in the task pool. It is called after the continuous task is complete. After the task is terminated, the thread that executes the task may be reclaimed. |

### Classes

| Name | Description |
| --- | --- |
| [AsyncRunner](arkts-arkts-taskpool-asyncrunner-c.md) | Implements an asynchronous queue, for which you can specify the task execution concurrency and queuing policy. |
| [GenericsTask](arkts-arkts-taskpool-genericstask-c.md) | Implements a generic task. **GenericsTask** inherits from [Task](arkts-arkts-taskpool-task-c.md). During the creation of a generic task, the passed-in parameter types and return value types of concurrent functions are verified in the compilation phase. Other behaviors are the same as those during the creation of a task. |
| [LongTask](arkts-arkts-taskpool-longtask-c.md) | Describes a continuous task. **LongTask** inherits from [Task](arkts-arkts-taskpool-task-c.md). No upper limit is set for the execution time of a continuous task, and no timeout exception is thrown if a continuous task runs for a long period of time. However, a continuous task cannot be executed in a task group or executed for multiple times. The thread for executing a continuous task exists until [terminateTask](arkts-arkts-taskpool-terminatetask-f.md) is called after the execution is complete. The thread is reclaimed when it is idle. |
| [SequenceRunner](arkts-arkts-taskpool-sequencerunner-c.md) | Implements a serial queue, in which all tasks are executed in sequence. |
| [Task](arkts-arkts-taskpool-task-c.md) | Enumerates tasks, which can be executed for multiple times, placed in a task group, serial queue, or asynchronous queue for execution, or added with dependencies for execution. |
| [TaskGroup](arkts-arkts-taskpool-taskgroup-c.md) | Implements a task group, in which tasks are associated with each other and all tasks are executed at a time. If all the tasks are executed normally, an array of task results is returned asynchronously, and the sequence of elements in the array is the same as the sequence of tasks added by calling [addTask](arkts-arkts-taskpool-taskgroup-c.md#addtask-1). If any task fails, the corresponding exception is thrown. If multiple tasks in the task group fail, the exception of the first failed task is thrown. A task group can be executed for multiple times, but no task can be added after the task group is executed. |
| [TaskInfo](arkts-arkts-taskpool-taskinfo-c.md) | Describes the internal information about a task. |
| [TaskPoolInfo](arkts-arkts-taskpool-taskpoolinfo-c.md) | Describes the internal information about a task pool. |
| [ThreadInfo](arkts-arkts-taskpool-threadinfo-c.md) | Describes the internal information about a worker thread. |

### Interfaces

| Name | Description |
| --- | --- |
| [Configs](arkts-arkts-taskpool-configs-i.md) | Defines the task configs interface |
| [TaskResult](arkts-arkts-taskpool-taskresult-i.md) | Describes the supplementary information captured in **BusinessError** in the catch branch after a task in the waiting or execution phase is canceled. In other scenarios, the task result is **undefined**. |

### Enums

| Name | Description |
| --- | --- |
| [Priority](arkts-arkts-taskpool-priority-e.md) | Enumerates the priorities available for created tasks. The task priority applies during task execution. The worker thread priority is updated with the task priority. For details about the mappings, see [QoS Level](../../../napi/qos-guidelines.md#qos-level). |
| [State](arkts-arkts-taskpool-state-e.md) | Enumerates the task states. After a task is created and **execute()** is called, the task is placed in the internal queue of the task pool and the state is **WAITING**. When the task is being executed by the worker thread of the task pool, the state changes to **RUNNING**. After the task is executed and the result is returned, the state is reset to **WAITING**. When the task is proactively canceled, the state changes to **CANCELED**. |

### Types

| Name | Description |
| --- | --- |
| [CallbackFunction](arkts-arkts-taskpool-callbackfunction-t.md) | Describes a callback function. |
| [CallbackFunctionWithError](arkts-arkts-taskpool-callbackfunctionwitherror-t.md) | Describes a callback function with an error message. |
